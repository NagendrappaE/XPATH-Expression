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

4.comparision:
a)number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId1)))=1   output:false
b)number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId)))=1     output:true
c) number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId1)))=1 and 2=1    output:false
d)number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId1)))=1 and 2=2   output:false
e)number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId1)))=1 and 2=2
f)number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId)))=1 and 2=2   output:true
g)number(boolean(name(//Body/executeFinacleScriptResponse/executeFinacleScript_CustomData/TrnId)))=1 and 2=3 output:false


5.XML Pathaxes:
a) //HostTransaction/descendant::*     output: SUCCESS
b) //ResponseMessageInfo/descendant::* output:   XXXX
GMT+05:30
2024-07-24T11:19:45.873
c)//ResponseMessageInfo/descendant::BankId  output:XXXX
d)//ResponseMessageInfo/ancestor::*   output:disaplyas all ancestors 

6.String function:

a)string('ee')   output: ee
b)string(2)  output:2
c)string(-0) output:0
d)concat('x','sss','ty',3,'5677')   output: xsssty35677
e) //RequestMessageKey/*[local-name()='RequestUUID']    output:XXXXXXX_USR_172180017283107
f)concat('NA',//RequestMessageKey/*[local-name()='RequestUUID'])  output: NAXXXXXXX_USR_172180017283107
g)concat('NA',//RequestMessageKey/*[local-name()='RequestUUID'],'QQ',string())  output:NAXXXXXXX_USR_172180017283107QQ XXXXXXX_USR_172180017283107 executeFinacleScript 10.2 XXX XXXX GMT+05:30 2024-07-24T11:19:45.873 SUCCESS

h)concat('NA',//RequestMessageKey/*[local-name()='RequestUUID'],'QQ',string(-0))  output:NAXXXXXXX_USR_172180017283107QQ0

i)concat('NA',//RequestMessageKey/*[local-name()='RequestUUID'],'QQ',string(-0),not(//NAA))   output: NAXXXXXXX_USR_172180017283107QQ0true
j)concat('NA',//RequestMessageKey/*[local-name()='RequestUUID'],'QQ',string(-0),not(//NAA),number(//GG))  output:NAXXXXXXX_USR_172180017283107QQ0trueNaN
k)concat('NA',//RequestMessageKey/*[local-name()='RequestUUID'],'QQ',string(-0),not(//NAA),number(not(//GG)))  output:NAXXXXXXX_USR_172180017283107QQ0true1
l)concat('NA',//RequestMessageKey/*[local-name()='RequestUUID'],'QQ',string(-0),not(//NAA),number(not(//GG))=1)   output:NAXXXXXXX_USR_172180017283107QQ0truetrue 
m)//*[local-name()='HostTransaction']/*[local-name()='Status']='SUCCESS'   output:true
n)//*[local-name()='HostTransaction']/*[local-name()='Status'][text()='SUCCESS']/ancestor::*[local-name()='Header']/following-sibling::*[local-name()='Body']/*[local-name()='executeFinacleScriptResponse']/*[local-name()='executeFinacleScript_CustomData']/*[local-name()='TrnId']

output:XXXXXXXX

o)//*[local-name()='HostTransaction']/*[local-name()='Status'][text()='SUCCESS1' or 1=1]/ancestor::*[local-name()='Header']/following-sibling::*[local-name()='Body']/*[local-name()='executeFinacleScriptResponse']/*[local-name()='executeFinacleScript_CustomData']/*[local-name()='TrnId']
 output:XXXXXXXX
p)//*[local-name()='HostTransaction']/*[local-name()='Status'][text()='SUCCESS1' or 1=3]/ancestor::*[local-name()='Header']/following-sibling::*[local-name()='Body']/*[local-name()='executeFinacleScriptResponse']/*[local-name()='executeFinacleScript_CustomData']/*[local-name()='TrnId']

output:  






