# XPATH-Expression
# online xpath link: https://www.freeformatter.com/xpath-tester.html#before-output
# Xpath version :https://www.w3.org/TR/1999/REC-xpath-19991116/#:~:text=XPath%20models%20an%20XML%20document,of%20nodes%20also%20have%20names.

sample XML:

<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<FIXML xmlns="http://www.finacle.com/fixml" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.finacle.com/fixml executeFinacleScript.xsd">

  <Header>
    <ResponseHeader>
      <RequestMessageKey>
        <RequestUUID>XXXXXXX_USR_172180017283107</RequestUUID>
        <ServiceRequestId>executeFinacleScript</ServiceRequestId>
        <ServiceRequestVersion>10.2</ServiceRequestVersion>
        <ChannelId>XXX</ChannelId>
      </RequestMessageKey>
      <ResponseMessageInfo>
        <BankId>XXXX</BankId>
        <TimeZone>GMT+05:30</TimeZone>
        <MessageDateTime>2024-07-24T11:19:45.873</MessageDateTime>
      </ResponseMessageInfo>
      <UBUSTransaction>
        <Id/>
        <Status/>
      </UBUSTransaction>
      <HostTransaction>
        <Id/>
        <Status>SUCCESS</Status>
      </HostTransaction>
      <HostParentTransaction>
        <Id/>
        <Status/>
      </HostParentTransaction>
      <CustomInfo/>
    </ResponseHeader>
  </Header>

  <Body>
    <executeFinacleScriptResponse>
      <ExecuteFinacleScriptOutputVO></ExecuteFinacleScriptOutputVO>
      <executeFinacleScript_CustomData>
        <TrnId>XXXXXXXX</TrnId>
        <TrnDt>24-07-2024</TrnDt>
      </executeFinacleScript_CustomData>
    </executeFinacleScriptResponse>
  </Body>

</FIXML>




example:

1.Get the Name of element:

 a) name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId)       output:TrnId
 b) name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId1)      output: ''

2.To get boolean Value :

a)boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId1))   output:false
b) boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId))    output:true

3.To  get number,true-1 and false-0

a) number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId1)))   output;0
b)number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId)))   output:1




