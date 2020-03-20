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
# <a name="sendmail-custom-activity"></a><span data-ttu-id="46b7f-102">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="46b7f-102">SendMail Custom Activity</span></span>
<span data-ttu-id="46b7f-103">此範例示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以便使用 SMTP 傳送郵件供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="46b7f-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="46b7f-104">自訂活動使用以<xref:System.Net.Mail.SmtpClient>非同步方式發送電子郵件和通過身份驗證發送郵件的功能。</span><span class="sxs-lookup"><span data-stu-id="46b7f-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="46b7f-105">也會提供一些終端使用者功能，例如測試模式、語彙基元替換、檔案範本和測試置放路徑。</span><span class="sxs-lookup"><span data-stu-id="46b7f-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="46b7f-106">下表詳細說明 `SendMail` 活動的引數。</span><span class="sxs-lookup"><span data-stu-id="46b7f-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="46b7f-107">名稱</span><span class="sxs-lookup"><span data-stu-id="46b7f-107">Name</span></span>|<span data-ttu-id="46b7f-108">類型</span><span class="sxs-lookup"><span data-stu-id="46b7f-108">Type</span></span>|<span data-ttu-id="46b7f-109">描述</span><span class="sxs-lookup"><span data-stu-id="46b7f-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="46b7f-110">Host</span><span class="sxs-lookup"><span data-stu-id="46b7f-110">Host</span></span>|<span data-ttu-id="46b7f-111">String</span><span class="sxs-lookup"><span data-stu-id="46b7f-111">String</span></span>|<span data-ttu-id="46b7f-112">SMTP 伺服器主機的位址。</span><span class="sxs-lookup"><span data-stu-id="46b7f-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="46b7f-113">連接埠</span><span class="sxs-lookup"><span data-stu-id="46b7f-113">Port</span></span>|<span data-ttu-id="46b7f-114">String</span><span class="sxs-lookup"><span data-stu-id="46b7f-114">String</span></span>|<span data-ttu-id="46b7f-115">SMTP 服務在主機中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="46b7f-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="46b7f-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="46b7f-116">EnableSsl</span></span>|<span data-ttu-id="46b7f-117">bool</span><span class="sxs-lookup"><span data-stu-id="46b7f-117">bool</span></span>|<span data-ttu-id="46b7f-118">指定 <xref:System.Net.Mail.SmtpClient> 是否使用 Secure Sockets Layer (SSL) 加密連接。</span><span class="sxs-lookup"><span data-stu-id="46b7f-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="46b7f-119">UserName</span><span class="sxs-lookup"><span data-stu-id="46b7f-119">UserName</span></span>|<span data-ttu-id="46b7f-120">String</span><span class="sxs-lookup"><span data-stu-id="46b7f-120">String</span></span>|<span data-ttu-id="46b7f-121">設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="46b7f-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="46b7f-122">密碼</span><span class="sxs-lookup"><span data-stu-id="46b7f-122">Password</span></span>|<span data-ttu-id="46b7f-123">String</span><span class="sxs-lookup"><span data-stu-id="46b7f-123">String</span></span>|<span data-ttu-id="46b7f-124">設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的密碼。</span><span class="sxs-lookup"><span data-stu-id="46b7f-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="46b7f-125">主體</span><span class="sxs-lookup"><span data-stu-id="46b7f-125">Subject</span></span>|<span data-ttu-id="46b7f-126"><xref:System.Activities.InArgument%601>\<字串></span><span class="sxs-lookup"><span data-stu-id="46b7f-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="46b7f-127">訊息的主旨。</span><span class="sxs-lookup"><span data-stu-id="46b7f-127">Subject of the message.</span></span>|  
|<span data-ttu-id="46b7f-128">body</span><span class="sxs-lookup"><span data-stu-id="46b7f-128">Body</span></span>|<span data-ttu-id="46b7f-129"><xref:System.Activities.InArgument%601>\<字串></span><span class="sxs-lookup"><span data-stu-id="46b7f-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="46b7f-130">訊息的本文。</span><span class="sxs-lookup"><span data-stu-id="46b7f-130">Body of the message.</span></span>|  
|<span data-ttu-id="46b7f-131">附件</span><span class="sxs-lookup"><span data-stu-id="46b7f-131">Attachments</span></span>|<span data-ttu-id="46b7f-132"><xref:System.Activities.InArgument%601>\<字串></span><span class="sxs-lookup"><span data-stu-id="46b7f-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="46b7f-133">用於存儲附加到此電子郵件的資料的附件集合。</span><span class="sxs-lookup"><span data-stu-id="46b7f-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="46b7f-134">從</span><span class="sxs-lookup"><span data-stu-id="46b7f-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="46b7f-135">此電子郵件的位址。</span><span class="sxs-lookup"><span data-stu-id="46b7f-135">From address for this email message.</span></span>|  
|<span data-ttu-id="46b7f-136">至</span><span class="sxs-lookup"><span data-stu-id="46b7f-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="46b7f-137">包含此電子郵件收件者的位址集合。</span><span class="sxs-lookup"><span data-stu-id="46b7f-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="46b7f-138">CC</span><span class="sxs-lookup"><span data-stu-id="46b7f-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="46b7f-139">包含此電子郵件的抄送 （CC） 收件者的位址集合。</span><span class="sxs-lookup"><span data-stu-id="46b7f-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="46b7f-140">BCC</span><span class="sxs-lookup"><span data-stu-id="46b7f-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="46b7f-141">包含此電子郵件的盲拷貝 （BCC） 收件者的位址集合。</span><span class="sxs-lookup"><span data-stu-id="46b7f-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="46b7f-142">權杖</span><span class="sxs-lookup"><span data-stu-id="46b7f-142">Tokens</span></span>|<span data-ttu-id="46b7f-143"><xref:System.Activities.InArgument%601><I\<字典字串，字串>></span><span class="sxs-lookup"><span data-stu-id="46b7f-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="46b7f-144">本文內所要取代的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="46b7f-144">Tokens to replace in the body.</span></span> <span data-ttu-id="46b7f-145">此功能可讓使用者在本文中指定某些值，而之後可由使用這個屬性所提供的語彙基元所取代。</span><span class="sxs-lookup"><span data-stu-id="46b7f-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="46b7f-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="46b7f-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="46b7f-147">String</span><span class="sxs-lookup"><span data-stu-id="46b7f-147">String</span></span>|<span data-ttu-id="46b7f-148">本文的範本路徑。</span><span class="sxs-lookup"><span data-stu-id="46b7f-148">Path of a template for the body.</span></span> <span data-ttu-id="46b7f-149">`SendMail` 活動會將這個檔案的內容複製到它的本文屬性。</span><span class="sxs-lookup"><span data-stu-id="46b7f-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="46b7f-150">此範本包含的語彙基元可由語彙基元屬性的內容所取代。</span><span class="sxs-lookup"><span data-stu-id="46b7f-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="46b7f-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="46b7f-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="46b7f-152">設置此屬性後，所有電子郵件都發送到其中指定的位址。</span><span class="sxs-lookup"><span data-stu-id="46b7f-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="46b7f-153">當測試工作流程時，並不適合使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="46b7f-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="46b7f-154">例如，當您希望確保所有電子郵件都發送而不發送給實際收件者時。</span><span class="sxs-lookup"><span data-stu-id="46b7f-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="46b7f-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="46b7f-155">TestDropPath</span></span>|<span data-ttu-id="46b7f-156">String</span><span class="sxs-lookup"><span data-stu-id="46b7f-156">String</span></span>|<span data-ttu-id="46b7f-157">設置此屬性後，所有電子郵件也會保存在指定的檔中。</span><span class="sxs-lookup"><span data-stu-id="46b7f-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="46b7f-158">此屬性用於在測試或調試工作流時使用，以確保傳出電子郵件的格式和內容是合適的。</span><span class="sxs-lookup"><span data-stu-id="46b7f-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="46b7f-159">方案內容</span><span class="sxs-lookup"><span data-stu-id="46b7f-159">Solution Contents</span></span>  
 <span data-ttu-id="46b7f-160">此方案包含兩個專案。</span><span class="sxs-lookup"><span data-stu-id="46b7f-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="46b7f-161">隨附此逐步解說的專案</span><span class="sxs-lookup"><span data-stu-id="46b7f-161">Project</span></span>|<span data-ttu-id="46b7f-162">描述</span><span class="sxs-lookup"><span data-stu-id="46b7f-162">Description</span></span>|<span data-ttu-id="46b7f-163">重要檔案</span><span class="sxs-lookup"><span data-stu-id="46b7f-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="46b7f-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="46b7f-164">SendMail</span></span>|<span data-ttu-id="46b7f-165">SendMail 活動</span><span class="sxs-lookup"><span data-stu-id="46b7f-165">The SendMail activity</span></span>|<span data-ttu-id="46b7f-166">1. SendMail.cs：主要活動的實施</span><span class="sxs-lookup"><span data-stu-id="46b7f-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="46b7f-167">2. 發送郵件設計器.xaml 和SendMailDesigner.xaml.cs：發送郵件活動的設計師</span><span class="sxs-lookup"><span data-stu-id="46b7f-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="46b7f-168">3. MailTemplateBody.htm：要發送的電子郵件的範本。</span><span class="sxs-lookup"><span data-stu-id="46b7f-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="46b7f-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="46b7f-169">SendMailTestClient</span></span>|<span data-ttu-id="46b7f-170">測試 SendMail 活動的用戶端。</span><span class="sxs-lookup"><span data-stu-id="46b7f-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="46b7f-171">此專案會示範兩個方式來叫用 SendMail 活動：宣告方式和程式設計方式。</span><span class="sxs-lookup"><span data-stu-id="46b7f-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="46b7f-172">1. 序列1.xaml：調用發送郵件活動的工作流。</span><span class="sxs-lookup"><span data-stu-id="46b7f-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="46b7f-173">2. Program.cs：調用 Sequence1，並以程式設計方式創建使用 SendMail 的工作流。</span><span class="sxs-lookup"><span data-stu-id="46b7f-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="46b7f-174">SendMail 活動的進一步組態設定</span><span class="sxs-lookup"><span data-stu-id="46b7f-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="46b7f-175">使用者可以執行 SendMail 活動的進一步組態設定，但是本範例並未顯示這個部分。</span><span class="sxs-lookup"><span data-stu-id="46b7f-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="46b7f-176">以下三節將示範如何進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="46b7f-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="46b7f-177">使用本文內指定的語彙基元傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="46b7f-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="46b7f-178">此程式碼片段會示範如何使用本文的語彙基元來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="46b7f-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="46b7f-179">請注意本文屬性內是如何提供語彙基元。</span><span class="sxs-lookup"><span data-stu-id="46b7f-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="46b7f-180">這些語彙基元的值會提供給語彙基元屬性。</span><span class="sxs-lookup"><span data-stu-id="46b7f-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="46b7f-181">使用範本傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="46b7f-181">Sending an email using a template</span></span>  
 <span data-ttu-id="46b7f-182">此程式碼片段會示範如何使用本文的範本語彙基元來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="46b7f-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="46b7f-183">請注意，當設定 `BodyTemplateFilePath` 屬性時，我們不需要為 Body 屬性提供值 (範本檔案的內容將會複製到本文)。</span><span class="sxs-lookup"><span data-stu-id="46b7f-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="46b7f-184">在測試模式下傳送郵件</span><span class="sxs-lookup"><span data-stu-id="46b7f-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="46b7f-185">此程式碼片段演示如何設置兩個測試屬性：通過設置`TestMailTo`到將發送到的所有消息`john.doe@contoso.con`（不考慮 To、Cc、密件副本的值）。</span><span class="sxs-lookup"><span data-stu-id="46b7f-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="46b7f-186">設定 TestDropPath 之後，所有外送的電子郵件也會記錄在提供的路徑上。</span><span class="sxs-lookup"><span data-stu-id="46b7f-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="46b7f-187">這些屬性可以獨立設定 (屬性之間並沒有相關性)。</span><span class="sxs-lookup"><span data-stu-id="46b7f-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="46b7f-188">設定指示</span><span class="sxs-lookup"><span data-stu-id="46b7f-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="46b7f-189">這個範例需要 SMTP 伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="46b7f-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="46b7f-190">有關設置 SMTP 伺服器的詳細資訊，請參閱以下連結。</span><span class="sxs-lookup"><span data-stu-id="46b7f-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="46b7f-191">[設定 SMTP 服務 (IIS 6.0) (英文)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="46b7f-191">[Configuring the SMTP Service (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="46b7f-192">[IIS 7.0：設定 SMTP 電子郵件](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="46b7f-192">[IIS 7.0: Configure SMTP E-Mail](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="46b7f-193">[如何安裝 SMTP 服務](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="46b7f-193">[How to Install the SMTP Service](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="46b7f-194">協力廠商提供的 SMTP 模擬器可供您下載。</span><span class="sxs-lookup"><span data-stu-id="46b7f-194">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="46b7f-195">執行此範例</span><span class="sxs-lookup"><span data-stu-id="46b7f-195">To run this sample</span></span>  
  
1. <span data-ttu-id="46b7f-196">使用 Visual Studio 2010，打開 SendMail.sln 解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="46b7f-196">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="46b7f-197">確定您可以存取有效的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="46b7f-197">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="46b7f-198">請參閱設定指示。</span><span class="sxs-lookup"><span data-stu-id="46b7f-198">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="46b7f-199">使用伺服器位址和"從"和"收件者"電子郵件地址配置程式。</span><span class="sxs-lookup"><span data-stu-id="46b7f-199">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="46b7f-200">要正確運行此示例，您可能需要在 Program.cs 和 Sequence.xaml 中配置"收件者"和"收件者"電子郵件地址的值以及 SMTP 伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="46b7f-200">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="46b7f-201">您需要在這兩個位置中變更地址，因為此程式會以兩個不同的方式傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="46b7f-201">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="46b7f-202">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="46b7f-202">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="46b7f-203">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="46b7f-203">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="46b7f-204">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="46b7f-204">The samples may already be installed on your machine.</span></span> <span data-ttu-id="46b7f-205">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="46b7f-205">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="46b7f-206">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="46b7f-206">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46b7f-207">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="46b7f-207">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
