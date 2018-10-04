---
title: SendMail 自訂活動
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: f51914ae01ea680ae09be8080cce1aa866bd6ec7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266661"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="2b373-102">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="2b373-102">SendMail Custom Activity</span></span>
<span data-ttu-id="2b373-103">此範例示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以便使用 SMTP 傳送郵件供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="2b373-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="2b373-104">自訂活動使用的功能<xref:System.Net.Mail.SmtpClient>以非同步方式傳送電子郵件並傳送具有驗證的郵件。</span><span class="sxs-lookup"><span data-stu-id="2b373-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="2b373-105">也會提供一些終端使用者功能，例如測試模式、語彙基元替換、檔案範本和測試置放路徑。</span><span class="sxs-lookup"><span data-stu-id="2b373-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="2b373-106">下表詳細說明 `SendMail` 活動的引數。</span><span class="sxs-lookup"><span data-stu-id="2b373-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="2b373-107">名稱</span><span class="sxs-lookup"><span data-stu-id="2b373-107">Name</span></span>|<span data-ttu-id="2b373-108">類型</span><span class="sxs-lookup"><span data-stu-id="2b373-108">Type</span></span>|<span data-ttu-id="2b373-109">描述</span><span class="sxs-lookup"><span data-stu-id="2b373-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2b373-110">主機</span><span class="sxs-lookup"><span data-stu-id="2b373-110">Host</span></span>|<span data-ttu-id="2b373-111">String</span><span class="sxs-lookup"><span data-stu-id="2b373-111">String</span></span>|<span data-ttu-id="2b373-112">SMTP 伺服器主機的位址。</span><span class="sxs-lookup"><span data-stu-id="2b373-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="2b373-113">通訊埠</span><span class="sxs-lookup"><span data-stu-id="2b373-113">Port</span></span>|<span data-ttu-id="2b373-114">String</span><span class="sxs-lookup"><span data-stu-id="2b373-114">String</span></span>|<span data-ttu-id="2b373-115">SMTP 服務在主機中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="2b373-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="2b373-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="2b373-116">EnableSsl</span></span>|<span data-ttu-id="2b373-117">bool</span><span class="sxs-lookup"><span data-stu-id="2b373-117">bool</span></span>|<span data-ttu-id="2b373-118">指定 <xref:System.Net.Mail.SmtpClient> 是否使用 Secure Sockets Layer (SSL) 加密連接。</span><span class="sxs-lookup"><span data-stu-id="2b373-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="2b373-119">UserName</span><span class="sxs-lookup"><span data-stu-id="2b373-119">UserName</span></span>|<span data-ttu-id="2b373-120">String</span><span class="sxs-lookup"><span data-stu-id="2b373-120">String</span></span>|<span data-ttu-id="2b373-121">設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2b373-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="2b373-122">密碼</span><span class="sxs-lookup"><span data-stu-id="2b373-122">Password</span></span>|<span data-ttu-id="2b373-123">String</span><span class="sxs-lookup"><span data-stu-id="2b373-123">String</span></span>|<span data-ttu-id="2b373-124">設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的密碼。</span><span class="sxs-lookup"><span data-stu-id="2b373-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="2b373-125">主旨</span><span class="sxs-lookup"><span data-stu-id="2b373-125">Subject</span></span>|<span data-ttu-id="2b373-126"><xref:System.Activities.InArgument%601>\<string></span><span class="sxs-lookup"><span data-stu-id="2b373-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="2b373-127">訊息的主旨。</span><span class="sxs-lookup"><span data-stu-id="2b373-127">Subject of the message.</span></span>|  
|<span data-ttu-id="2b373-128">本文</span><span class="sxs-lookup"><span data-stu-id="2b373-128">Body</span></span>|<span data-ttu-id="2b373-129"><xref:System.Activities.InArgument%601>\<string></span><span class="sxs-lookup"><span data-stu-id="2b373-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="2b373-130">訊息的本文。</span><span class="sxs-lookup"><span data-stu-id="2b373-130">Body of the message.</span></span>|  
|<span data-ttu-id="2b373-131">附件</span><span class="sxs-lookup"><span data-stu-id="2b373-131">Attachments</span></span>|<span data-ttu-id="2b373-132"><xref:System.Activities.InArgument%601>\<string></span><span class="sxs-lookup"><span data-stu-id="2b373-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="2b373-133">用來儲存資料附加到這個電子郵件訊息的附件集合。</span><span class="sxs-lookup"><span data-stu-id="2b373-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="2b373-134">從</span><span class="sxs-lookup"><span data-stu-id="2b373-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="2b373-135">從這個電子郵件訊息的位址。</span><span class="sxs-lookup"><span data-stu-id="2b373-135">From address for this email message.</span></span>|  
|<span data-ttu-id="2b373-136">以</span><span class="sxs-lookup"><span data-stu-id="2b373-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="2b373-137">包含此電子郵件訊息的收件者的地址集合。</span><span class="sxs-lookup"><span data-stu-id="2b373-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="2b373-138">CC</span><span class="sxs-lookup"><span data-stu-id="2b373-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="2b373-139">地址集合，其中包含這個電子郵件訊息的密件副本 (CC) 收件者。</span><span class="sxs-lookup"><span data-stu-id="2b373-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="2b373-140">BCC</span><span class="sxs-lookup"><span data-stu-id="2b373-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="2b373-141">包含此電子郵件訊息的密件副本 (BCC) 收件者的地址集合。</span><span class="sxs-lookup"><span data-stu-id="2b373-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="2b373-142">語彙基元</span><span class="sxs-lookup"><span data-stu-id="2b373-142">Tokens</span></span>|<span data-ttu-id="2b373-143"><xref:System.Activities.InArgument%601>< IDictionary\<，string> >></span><span class="sxs-lookup"><span data-stu-id="2b373-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="2b373-144">本文內所要取代的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2b373-144">Tokens to replace in the body.</span></span> <span data-ttu-id="2b373-145">此功能可讓使用者在本文中指定某些值，而之後可由使用這個屬性所提供的語彙基元所取代。</span><span class="sxs-lookup"><span data-stu-id="2b373-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="2b373-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="2b373-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="2b373-147">String</span><span class="sxs-lookup"><span data-stu-id="2b373-147">String</span></span>|<span data-ttu-id="2b373-148">本文的範本路徑。</span><span class="sxs-lookup"><span data-stu-id="2b373-148">Path of a template for the body.</span></span> <span data-ttu-id="2b373-149">`SendMail` 活動會將這個檔案的內容複製到它的本文屬性。</span><span class="sxs-lookup"><span data-stu-id="2b373-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="2b373-150">此範本包含的語彙基元可由語彙基元屬性的內容所取代。</span><span class="sxs-lookup"><span data-stu-id="2b373-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="2b373-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="2b373-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="2b373-152">當設定這個屬性時，所有的電子郵件會傳送指定的地址。</span><span class="sxs-lookup"><span data-stu-id="2b373-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="2b373-153">當測試工作流程時，並不適合使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="2b373-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="2b373-154">例如，當您想要確定所有電子郵件會傳送而不將它們傳送到實際的收件者。</span><span class="sxs-lookup"><span data-stu-id="2b373-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="2b373-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="2b373-155">TestDropPath</span></span>|<span data-ttu-id="2b373-156">String</span><span class="sxs-lookup"><span data-stu-id="2b373-156">String</span></span>|<span data-ttu-id="2b373-157">當設定這個屬性時，所有電子郵件也會儲存在指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="2b373-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="2b373-158">這個屬性被要在測試或偵錯工作流程，並確定的格式和外寄電子郵件的內容是適當時使用。</span><span class="sxs-lookup"><span data-stu-id="2b373-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="2b373-159">方案內容</span><span class="sxs-lookup"><span data-stu-id="2b373-159">Solution Contents</span></span>  
 <span data-ttu-id="2b373-160">此方案包含兩個專案。</span><span class="sxs-lookup"><span data-stu-id="2b373-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="2b373-161">Project</span><span class="sxs-lookup"><span data-stu-id="2b373-161">Project</span></span>|<span data-ttu-id="2b373-162">描述</span><span class="sxs-lookup"><span data-stu-id="2b373-162">Description</span></span>|<span data-ttu-id="2b373-163">重要檔案</span><span class="sxs-lookup"><span data-stu-id="2b373-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="2b373-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="2b373-164">SendMail</span></span>|<span data-ttu-id="2b373-165">SendMail 活動</span><span class="sxs-lookup"><span data-stu-id="2b373-165">The SendMail activity</span></span>|<span data-ttu-id="2b373-166">1.SendMail.cs：主要活動的實作</span><span class="sxs-lookup"><span data-stu-id="2b373-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="2b373-167">2.SendMailDesigner.xaml 和 SendMailDesigner.xaml.cs：SendMail 活動的設計工具</span><span class="sxs-lookup"><span data-stu-id="2b373-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="2b373-168">3.MailTemplateBody.htm：要外送之電子郵件的範本。</span><span class="sxs-lookup"><span data-stu-id="2b373-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="2b373-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="2b373-169">SendMailTestClient</span></span>|<span data-ttu-id="2b373-170">測試 SendMail 活動的用戶端。</span><span class="sxs-lookup"><span data-stu-id="2b373-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="2b373-171">此專案會示範兩個方式來叫用 SendMail 活動：宣告方式和程式設計方式。</span><span class="sxs-lookup"><span data-stu-id="2b373-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="2b373-172">1.Sequence1.xaml：叫用 SendMail 活動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="2b373-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="2b373-173">2.Program.cs：叫用 Sequence1 並以程式設計方式建立一個使用 SendMail 的工作流程。</span><span class="sxs-lookup"><span data-stu-id="2b373-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="2b373-174">SendMail 活動的進一步組態設定</span><span class="sxs-lookup"><span data-stu-id="2b373-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="2b373-175">使用者可以執行 SendMail 活動的進一步組態設定，但是本範例並未顯示這個部分。</span><span class="sxs-lookup"><span data-stu-id="2b373-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="2b373-176">以下三節將示範如何進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="2b373-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="2b373-177">使用本文內指定的語彙基元傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="2b373-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="2b373-178">此程式碼片段會示範如何使用本文的語彙基元來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="2b373-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="2b373-179">請注意本文屬性內是如何提供語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2b373-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="2b373-180">這些語彙基元的值會提供給語彙基元屬性。</span><span class="sxs-lookup"><span data-stu-id="2b373-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```html  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="2b373-181">使用範本傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="2b373-181">Sending an email using a template</span></span>  
 <span data-ttu-id="2b373-182">此程式碼片段會示範如何使用本文的範本語彙基元來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="2b373-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="2b373-183">請注意，當設定 `BodyTemplateFilePath` 屬性時，我們不需要為 Body 屬性提供值 (範本檔案的內容將會複製到本文)。</span><span class="sxs-lookup"><span data-stu-id="2b373-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="2b373-184">在測試模式下傳送郵件</span><span class="sxs-lookup"><span data-stu-id="2b373-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="2b373-185">此程式碼片段示範如何設定兩個測試的屬性： 藉由設定`TestMailTo`所有的訊息將傳送至john.doe@contoso.con（而不考慮的值、 副本、 密件副本）。</span><span class="sxs-lookup"><span data-stu-id="2b373-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="2b373-186">設定 TestDropPath 之後，所有外送的電子郵件也會記錄在提供的路徑上。</span><span class="sxs-lookup"><span data-stu-id="2b373-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="2b373-187">這些屬性可以獨立設定 (屬性之間並沒有相關性)。</span><span class="sxs-lookup"><span data-stu-id="2b373-187">These properties can be set independently (they are not related).</span></span>  
  
```  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="2b373-188">設定指示</span><span class="sxs-lookup"><span data-stu-id="2b373-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="2b373-189">這個範例需要 SMTP 伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="2b373-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="2b373-190">如需有關設定 SMTP 伺服器的詳細資訊，請參閱下列連結。</span><span class="sxs-lookup"><span data-stu-id="2b373-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="2b373-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="2b373-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="2b373-192">設定 SMTP 服務 (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="2b373-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="2b373-193">IIS 7.0： 設定 SMTP 電子郵件</span><span class="sxs-lookup"><span data-stu-id="2b373-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="2b373-194">如何安裝 SMTP 服務</span><span class="sxs-lookup"><span data-stu-id="2b373-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="2b373-195">協力廠商提供的 SMTP 模擬器可供您下載。</span><span class="sxs-lookup"><span data-stu-id="2b373-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="2b373-196">若要執行這個範例</span><span class="sxs-lookup"><span data-stu-id="2b373-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="2b373-197">使用 Visual Studio 2010 開啟 SendMail.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="2b373-197">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2b373-198">確定您可以存取有效的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2b373-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="2b373-199">請參閱設定指示。</span><span class="sxs-lookup"><span data-stu-id="2b373-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="2b373-200">使用您的伺服器位址，以及從和電子郵件地址，請設定程式。</span><span class="sxs-lookup"><span data-stu-id="2b373-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="2b373-201">若要正確執行此範例中，您可能需要在 Program.cs 和 Sequence.xaml 中設定電子郵件地址以及 SMTP 伺服器的位址的值。</span><span class="sxs-lookup"><span data-stu-id="2b373-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="2b373-202">您需要在這兩個位置中變更地址，因為此程式會以兩個不同的方式傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="2b373-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="2b373-203">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="2b373-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="2b373-204">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="2b373-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2b373-205">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2b373-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2b373-206">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="2b373-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2b373-207">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="2b373-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2b373-208">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="2b373-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`