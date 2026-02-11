# EventID 1 Investigation (Sysmon)

## Context

During the lab setup, Sysmon was reinstalled to ensure that configuration changes were properly applied and to rule out service or driver inconsistencies.

This step was performed after validating that Splunk Universal Forwarder and event forwarding were functioning correctly.

## Sysmon Reinstallation

Sysmon was fully removed and reinstalled using the `sysmon-config.xml` configuration file.

The removal process successfully stopped and removed:

- The Sysmon64 service.
- The Sysmon driver (SysmonDrv).

A warning was observed indicating that `C:\Windows\Sysmon64.exe` could not be deleted.

![Sysmon could not be deleted](../images/doc05/sysmon-could-not-be-deleted.png)

This behavior is common on Windows systems and did not affect the reinstallation process.

Reinstallation was completed successfully using:

- XML schema validation.
- Service and driver startup without errors.

Service status verification confirmed:

- Sysmon64 service running.

This confirms that Sysmon was correctly installed and actively monitoring the system.

![Sysmon reinstallation ](../images/doc05/sysmon-reinstallation.png)

## XML Configuration Adjustments

To explicitly enable Process Creation telemetry, the Sysmon configuration file was modified during the investigation.

![XML Configuration Adjustments](../images/doc05/xml-configuration-adjustments.png)

The following rule was added to the XML configuration:

```XML
<Sysmon schemaversion="4.90">

  <HashAlgorithms>sha256</HashAlgorithms>

  <EventFiltering>

    <!-- Process Creation -->
    <ProcessCreate onmatch="include">
      <CommandLine condition="is">*</CommandLine>
    </ProcessCreate>

    <!-- Process Termination -->
    <ProcessTerminate onmatch="include" />

    <!-- Network Connections -->
    <NetworkConnect onmatch="include" />

    <!-- File Creation -->
    <FileCreate onmatch="include" />

    <!-- Registry Changes -->
    <RegistryEvent onmatch="include" />

  </EventFiltering>

</Sysmon>
```

This change was intended to ensure that all process creation events, including command-line data, were collected by Sysmon.

After applying the updated configuration:

- Sysmon accepted the XML without validation errors.
- The service restarted successfully.
- Existing Sysmon events continued to be generated.

These results confirmed that the configuration change was syntactically correct and successfully applied.

## Observed Behavior

Following reinstallation and configuration adjustments, Sysmon consistently generated multiple event types, including:

- `EventID 4`
- `EventID 5`
- `EventID 16`

This confirmed that Sysmon telemetry was active and being collected.

![Observed Behavior](../images/doc05/observed-behavior.png)

However, `EventID 1` (Process Creation) was not consistently observed in this environment, despite:

- Explicit inclusion in the XML configuration.
- Successful Sysmon service operation.
- Verified event forwarding to Splunk.

This behavior appears to be dependent on environmental factors, Sysmon version behavior, or the nature of the generated activity, rather than an indication of a logging or forwarding failure.

## Conclusion

The logging pipeline (Sysmon → Splunk Universal Forwarder → Splunk Enterprise) was **confirmed to be fully operational**.

While `EventID 1` was not reliably generated in this setup, other Sysmon events validated correct installation, configuration, and data ingestion.

![EventID1 no results found](../images/doc05/EventID1-no-results-found.png)

For the purposes of this lab, Sysmon was considered functional, and the investigation was documented to record observed limitations before proceeding with alternative event sources. **Note** I even try *Time range: All time* and nothing.
