# logback-msteams-appender-plus
A logback appender to push message to Microsoft Teams.

# Main Feature
- Push log inforamtion to Micirosoft Teams through webhook;
- Asynch http by using OkHttp;
- Support proxy and proxy authenctication;
- Support displaying exceptoin stack trace lines;

# How to use
Just configure a new appener into logback configuration

```xml
<appender name="MSTEAMS" class="me.danielpf.logbackappender.msteams.MsTeamsAppender">
    <!-- Webhook URI, required -->
    <webHookUri>${Your Webhook URI}</webHookUri>
    <!-- Custom connection timeout, default 5 seconds, TimeUint: millisecond -->
    <connectTimeout>1000</connectTimeout>
    <!-- Custom read timeout, default 10 seconds, TimeUint: millisecond -->
    <readTimeout>3000</readTimeout>
    <!-- Custom write timeout, default 10 seconds, TimeUint: millisecond -->
    <readTimeout>3000</readTimeout>
    <!-- a prefix will be ahead of entire title, which can identify the app or env information -->
    <titlePrefix>Staging</titlePrefix>
        
    <!-- Proxy Configuration -->
    <proxyHost>${Your Proxy Host}</proxyHost>
    <proxyPort>${Your Proxy Port}</proxyPort>
    <proxyUsername>${Your Proxy Username}</proxyUsername>
    <proxyPassword>${Your Proxy Password}</proxyPassword>
    
    <!-- how many lines will be displayed in the message body, default is 5 -->
    <stackTraceLines>5</stackTraceLines>
</appender>

<!-- Currently recommended way of using MS Teams appender -->
<appender name="ASYNC_MSTEAMS" class="ch.qos.logback.classic.AsyncAppender">
    <appender-ref ref="MSTEAMS"/>
    <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
        <level>ERROR</level>
    </filter>
</appender>

```

# Demo
![Image of Demo](./demo.jpg)

# Acknowledgements
Thanks @michl-b and @mmaeller, some ideas were coming from your codebase. 


# Reference
[Sending messages to connectors and webhooks](https://docs.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/connectors-using)

