---
title: SendMail 自訂活動
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: f518beebe336080853e4dec3bca6f8539bbec304
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267582"
---
# <a name="sendmail-custom-activity"></a>SendMail 自訂活動

此範例示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以便使用 SMTP 傳送郵件供工作流程應用程式使用。 自訂活動會使用的功能， <xref:System.Net.Mail.SmtpClient> 以非同步方式傳送電子郵件，並傳送含有驗證的電子郵件。 也會提供一些終端使用者功能，例如測試模式、語彙基元替換、檔案範本和測試置放路徑。  
  
 下表詳細說明 `SendMail` 活動的引數。  
  
|名稱|類型|描述|  
|-|-|-|  
|主機|字串|SMTP 伺服器主機的位址。|  
|連接埠|字串|SMTP 服務在主機中的連接埠。|  
|EnableSsl|bool|指定 <xref:System.Net.Mail.SmtpClient> 是否使用 Secure Sockets Layer (SSL) 加密連接。|  
|UserName|字串|設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的使用者名稱。|  
|密碼|字串|設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的密碼。|  
|主體|<xref:System.Activities.InArgument%601>\<string>|訊息的主旨。|  
|主體|<xref:System.Activities.InArgument%601>\<string>|訊息的本文。|  
|附件|<xref:System.Activities.InArgument%601>\<string>|用來儲存附加到這個電子郵件訊息之資料的附件集合。|  
|寄件者|<xref:System.Net.Mail.MailAddress>|這封電子郵件訊息的寄件者位址。|  
|收件者|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|包含此電子郵件訊息之收件者的位址集合。|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|包含此電子郵件訊息之副本 (CC) 收件者的位址集合。|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|包含此電子郵件訊息之密件 (抄送) 收件者的位址集合。|  
|權杖|<xref:System.Activities.InArgument%601><IDictionary\<string, string>>|本文內所要取代的語彙基元。 此功能可讓使用者在本文中指定某些值，而之後可由使用這個屬性所提供的語彙基元所取代。|  
|BodyTemplateFilePath|字串|本文的範本路徑。 `SendMail` 活動會將這個檔案的內容複製到它的本文屬性。<br /><br /> 此範本包含的語彙基元可由語彙基元屬性的內容所取代。|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|當設定此屬性時，所有電子郵件都會傳送至其中指定的位址。<br /><br /> 當測試工作流程時，並不適合使用這個屬性。 例如，當您想要確保所有電子郵件都傳送出去，而不將它們傳送給實際的收件者。|  
|TestDropPath|字串|當設定這個屬性時，所有電子郵件也會儲存在指定的檔案中。<br /><br /> 當您要測試或偵測工作流程時，可以使用這個屬性，以確保外寄電子郵件的格式和內容都適用。|  
  
## <a name="solution-contents"></a>方案內容  

 此方案包含兩個專案。  
  
|專案|描述|重要檔案|  
|-------------|-----------------|---------------------|  
|SendMail|SendMail 活動|1. SendMail.cs：主要活動的執行<br />SendMailDesigner 和 SendMailDesigner.xaml.cs： SendMail 活動的設計工具<br />3. MailTemplateBody.htm：要送出之電子郵件的範本。|  
|SendMailTestClient|測試 SendMail 活動的用戶端。  此專案會示範兩個方式來叫用 SendMail 活動：宣告方式和程式設計方式。|Sequence1：調用 SendMail 活動的工作流程。<br />2. Program.cs：叫用 Sequence1，也會以程式設計方式使用 SendMail 來建立工作流程。|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>SendMail 活動的進一步組態設定  

 使用者可以執行 SendMail 活動的進一步組態設定，但是本範例並未顯示這個部分。 以下三節將示範如何進行這項處理。  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>使用本文內指定的語彙基元傳送電子郵件  

 此程式碼片段會示範如何使用本文的語彙基元來傳送電子郵件。 請注意本文屬性內是如何提供語彙基元。 這些語彙基元的值會提供給語彙基元屬性。  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a>使用範本傳送電子郵件  

 此程式碼片段會示範如何使用本文的範本語彙基元來傳送電子郵件。 請注意，當設定 `BodyTemplateFilePath` 屬性時，我們不需要為 Body 屬性提供值 (範本檔案的內容將會複製到本文)。  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a>在測試模式下傳送郵件  

 此程式碼片段示範如何設定這兩個測試屬性：將設定 `TestMailTo` 為 [所有訊息] 將傳送至 `john.doe@contoso.con` (，而不考慮 [收件者]、[副本]、[密件副本]) 的值。 設定 TestDropPath 之後，所有外送的電子郵件也會記錄在提供的路徑上。 這些屬性可以獨立設定 (屬性之間並沒有相關性)。  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a>設定指示  

 這個範例需要 SMTP 伺服器的存取權。  
  
 如需設定 SMTP 伺服器的詳細資訊，請參閱下列連結。  
  
- [設定 SMTP 服務 (IIS 6.0) (英文)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7.0：設定 SMTP 電子郵件](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [如何安裝 SMTP 服務](/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
 協力廠商提供的 SMTP 模擬器可供您下載。  
  
##### <a name="to-run-this-sample"></a>執行此範例  
  
1. 使用 Visual Studio 2010，開啟 [SendMail] 方案檔。  
  
2. 確定您可以存取有效的 SMTP 伺服器。 請參閱設定指示。  
  
3. 使用您的伺服器位址，以及從和傳送電子郵件地址來設定程式。  
  
     若要正確執行此範例，您可能需要將的值設定為 [寄件者] 和 [寄件者] 的電子郵件地址和 SMTP 伺服器位址，並依序 Program.cs 和。 您需要在這兩個位置中變更地址，因為此程式會以兩個不同的方式傳送郵件。  
  
4. 若要建置此方案，請按 CTRL+SHIFT+B。  
  
5. 若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
