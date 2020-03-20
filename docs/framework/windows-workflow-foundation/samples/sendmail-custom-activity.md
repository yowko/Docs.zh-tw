---
title: SendMail 自訂活動
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e7cc64e68c3d78b9ee7ec813700e96a52c239141
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182775"
---
# <a name="sendmail-custom-activity"></a>SendMail 自訂活動
此範例示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以便使用 SMTP 傳送郵件供工作流程應用程式使用。 自訂活動使用以<xref:System.Net.Mail.SmtpClient>非同步方式發送電子郵件和通過身份驗證發送郵件的功能。 也會提供一些終端使用者功能，例如測試模式、語彙基元替換、檔案範本和測試置放路徑。  
  
 下表詳細說明 `SendMail` 活動的引數。  
  
|名稱|類型|描述|  
|-|-|-|  
|Host|String|SMTP 伺服器主機的位址。|  
|連接埠|String|SMTP 服務在主機中的連接埠。|  
|EnableSsl|bool|指定 <xref:System.Net.Mail.SmtpClient> 是否使用 Secure Sockets Layer (SSL) 加密連接。|  
|UserName|String|設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的使用者名稱。|  
|密碼|String|設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的密碼。|  
|主體|<xref:System.Activities.InArgument%601>\<字串>|訊息的主旨。|  
|body|<xref:System.Activities.InArgument%601>\<字串>|訊息的本文。|  
|附件|<xref:System.Activities.InArgument%601>\<字串>|用於存儲附加到此電子郵件的資料的附件集合。|  
|從|<xref:System.Net.Mail.MailAddress>|此電子郵件的位址。|  
|至|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|包含此電子郵件收件者的位址集合。|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|包含此電子郵件的抄送 （CC） 收件者的位址集合。|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|包含此電子郵件的盲拷貝 （BCC） 收件者的位址集合。|  
|權杖|<xref:System.Activities.InArgument%601><I\<字典字串，字串>>|本文內所要取代的語彙基元。 此功能可讓使用者在本文中指定某些值，而之後可由使用這個屬性所提供的語彙基元所取代。|  
|BodyTemplateFilePath|String|本文的範本路徑。 `SendMail` 活動會將這個檔案的內容複製到它的本文屬性。<br /><br /> 此範本包含的語彙基元可由語彙基元屬性的內容所取代。|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|設置此屬性後，所有電子郵件都發送到其中指定的位址。<br /><br /> 當測試工作流程時，並不適合使用這個屬性。 例如，當您希望確保所有電子郵件都發送而不發送給實際收件者時。|  
|TestDropPath|String|設置此屬性後，所有電子郵件也會保存在指定的檔中。<br /><br /> 此屬性用於在測試或調試工作流時使用，以確保傳出電子郵件的格式和內容是合適的。|  
  
## <a name="solution-contents"></a>方案內容  
 此方案包含兩個專案。  
  
|隨附此逐步解說的專案|描述|重要檔案|  
|-------------|-----------------|---------------------|  
|SendMail|SendMail 活動|1. SendMail.cs：主要活動的實施<br />2. 發送郵件設計器.xaml 和SendMailDesigner.xaml.cs：發送郵件活動的設計師<br />3. MailTemplateBody.htm：要發送的電子郵件的範本。|  
|SendMailTestClient|測試 SendMail 活動的用戶端。  此專案會示範兩個方式來叫用 SendMail 活動：宣告方式和程式設計方式。|1. 序列1.xaml：調用發送郵件活動的工作流。<br />2. Program.cs：調用 Sequence1，並以程式設計方式創建使用 SendMail 的工作流。|  
  
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
 此程式碼片段演示如何設置兩個測試屬性：通過設置`TestMailTo`到將發送到的所有消息`john.doe@contoso.con`（不考慮 To、Cc、密件副本的值）。 設定 TestDropPath 之後，所有外送的電子郵件也會記錄在提供的路徑上。 這些屬性可以獨立設定 (屬性之間並沒有相關性)。  
  
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
  
 有關設置 SMTP 伺服器的詳細資訊，請參閱以下連結。  
  
- [設定 SMTP 服務 (IIS 6.0) (英文)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7.0：設定 SMTP 電子郵件](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [如何安裝 SMTP 服務](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
 協力廠商提供的 SMTP 模擬器可供您下載。  
  
##### <a name="to-run-this-sample"></a>執行此範例  
  
1. 使用 Visual Studio 2010，打開 SendMail.sln 解決方案檔。  
  
2. 確定您可以存取有效的 SMTP 伺服器。 請參閱設定指示。  
  
3. 使用伺服器位址和"從"和"收件者"電子郵件地址配置程式。  
  
     要正確運行此示例，您可能需要在 Program.cs 和 Sequence.xaml 中配置"收件者"和"收件者"電子郵件地址的值以及 SMTP 伺服器的位址。 您需要在這兩個位置中變更地址，因為此程式會以兩個不同的方式傳送郵件。  
  
4. 若要建置此方案，請按 CTRL+SHIFT+B。  
  
5. 若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
