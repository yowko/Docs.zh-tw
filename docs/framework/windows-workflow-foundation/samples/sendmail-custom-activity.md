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
# <a name="sendmail-custom-activity"></a><span data-ttu-id="a7d3d-102">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="a7d3d-102">SendMail Custom Activity</span></span>

<span data-ttu-id="a7d3d-103">此範例示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以便使用 SMTP 傳送郵件供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="a7d3d-104">自訂活動會使用的功能， <xref:System.Net.Mail.SmtpClient> 以非同步方式傳送電子郵件，並傳送含有驗證的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="a7d3d-105">也會提供一些終端使用者功能，例如測試模式、語彙基元替換、檔案範本和測試置放路徑。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="a7d3d-106">下表詳細說明 `SendMail` 活動的引數。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="a7d3d-107">名稱</span><span class="sxs-lookup"><span data-stu-id="a7d3d-107">Name</span></span>|<span data-ttu-id="a7d3d-108">類型</span><span class="sxs-lookup"><span data-stu-id="a7d3d-108">Type</span></span>|<span data-ttu-id="a7d3d-109">描述</span><span class="sxs-lookup"><span data-stu-id="a7d3d-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a7d3d-110">主機</span><span class="sxs-lookup"><span data-stu-id="a7d3d-110">Host</span></span>|<span data-ttu-id="a7d3d-111">字串</span><span class="sxs-lookup"><span data-stu-id="a7d3d-111">String</span></span>|<span data-ttu-id="a7d3d-112">SMTP 伺服器主機的位址。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="a7d3d-113">連接埠</span><span class="sxs-lookup"><span data-stu-id="a7d3d-113">Port</span></span>|<span data-ttu-id="a7d3d-114">字串</span><span class="sxs-lookup"><span data-stu-id="a7d3d-114">String</span></span>|<span data-ttu-id="a7d3d-115">SMTP 服務在主機中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="a7d3d-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="a7d3d-116">EnableSsl</span></span>|<span data-ttu-id="a7d3d-117">bool</span><span class="sxs-lookup"><span data-stu-id="a7d3d-117">bool</span></span>|<span data-ttu-id="a7d3d-118">指定 <xref:System.Net.Mail.SmtpClient> 是否使用 Secure Sockets Layer (SSL) 加密連接。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="a7d3d-119">UserName</span><span class="sxs-lookup"><span data-stu-id="a7d3d-119">UserName</span></span>|<span data-ttu-id="a7d3d-120">字串</span><span class="sxs-lookup"><span data-stu-id="a7d3d-120">String</span></span>|<span data-ttu-id="a7d3d-121">設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="a7d3d-122">密碼</span><span class="sxs-lookup"><span data-stu-id="a7d3d-122">Password</span></span>|<span data-ttu-id="a7d3d-123">字串</span><span class="sxs-lookup"><span data-stu-id="a7d3d-123">String</span></span>|<span data-ttu-id="a7d3d-124">設定認證來驗證寄件者 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 屬性的密碼。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="a7d3d-125">主體</span><span class="sxs-lookup"><span data-stu-id="a7d3d-125">Subject</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="a7d3d-126">訊息的主旨。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-126">Subject of the message.</span></span>|  
|<span data-ttu-id="a7d3d-127">主體</span><span class="sxs-lookup"><span data-stu-id="a7d3d-127">Body</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="a7d3d-128">訊息的本文。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-128">Body of the message.</span></span>|  
|<span data-ttu-id="a7d3d-129">附件</span><span class="sxs-lookup"><span data-stu-id="a7d3d-129">Attachments</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="a7d3d-130">用來儲存附加到這個電子郵件訊息之資料的附件集合。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-130">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="a7d3d-131">寄件者</span><span class="sxs-lookup"><span data-stu-id="a7d3d-131">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="a7d3d-132">這封電子郵件訊息的寄件者位址。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-132">From address for this email message.</span></span>|  
|<span data-ttu-id="a7d3d-133">收件者</span><span class="sxs-lookup"><span data-stu-id="a7d3d-133">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="a7d3d-134">包含此電子郵件訊息之收件者的位址集合。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-134">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="a7d3d-135">CC</span><span class="sxs-lookup"><span data-stu-id="a7d3d-135">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="a7d3d-136">包含此電子郵件訊息之副本 (CC) 收件者的位址集合。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-136">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="a7d3d-137">BCC</span><span class="sxs-lookup"><span data-stu-id="a7d3d-137">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="a7d3d-138">包含此電子郵件訊息之密件 (抄送) 收件者的位址集合。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-138">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="a7d3d-139">權杖</span><span class="sxs-lookup"><span data-stu-id="a7d3d-139">Tokens</span></span>|<span data-ttu-id="a7d3d-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span><span class="sxs-lookup"><span data-stu-id="a7d3d-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="a7d3d-141">本文內所要取代的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-141">Tokens to replace in the body.</span></span> <span data-ttu-id="a7d3d-142">此功能可讓使用者在本文中指定某些值，而之後可由使用這個屬性所提供的語彙基元所取代。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-142">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="a7d3d-143">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="a7d3d-143">BodyTemplateFilePath</span></span>|<span data-ttu-id="a7d3d-144">字串</span><span class="sxs-lookup"><span data-stu-id="a7d3d-144">String</span></span>|<span data-ttu-id="a7d3d-145">本文的範本路徑。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-145">Path of a template for the body.</span></span> <span data-ttu-id="a7d3d-146">`SendMail` 活動會將這個檔案的內容複製到它的本文屬性。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-146">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="a7d3d-147">此範本包含的語彙基元可由語彙基元屬性的內容所取代。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-147">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="a7d3d-148">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="a7d3d-148">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="a7d3d-149">當設定此屬性時，所有電子郵件都會傳送至其中指定的位址。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-149">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="a7d3d-150">當測試工作流程時，並不適合使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-150">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="a7d3d-151">例如，當您想要確保所有電子郵件都傳送出去，而不將它們傳送給實際的收件者。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-151">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="a7d3d-152">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="a7d3d-152">TestDropPath</span></span>|<span data-ttu-id="a7d3d-153">字串</span><span class="sxs-lookup"><span data-stu-id="a7d3d-153">String</span></span>|<span data-ttu-id="a7d3d-154">當設定這個屬性時，所有電子郵件也會儲存在指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-154">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="a7d3d-155">當您要測試或偵測工作流程時，可以使用這個屬性，以確保外寄電子郵件的格式和內容都適用。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-155">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="a7d3d-156">方案內容</span><span class="sxs-lookup"><span data-stu-id="a7d3d-156">Solution Contents</span></span>  

 <span data-ttu-id="a7d3d-157">此方案包含兩個專案。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-157">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="a7d3d-158">專案</span><span class="sxs-lookup"><span data-stu-id="a7d3d-158">Project</span></span>|<span data-ttu-id="a7d3d-159">描述</span><span class="sxs-lookup"><span data-stu-id="a7d3d-159">Description</span></span>|<span data-ttu-id="a7d3d-160">重要檔案</span><span class="sxs-lookup"><span data-stu-id="a7d3d-160">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="a7d3d-161">SendMail</span><span class="sxs-lookup"><span data-stu-id="a7d3d-161">SendMail</span></span>|<span data-ttu-id="a7d3d-162">SendMail 活動</span><span class="sxs-lookup"><span data-stu-id="a7d3d-162">The SendMail activity</span></span>|<span data-ttu-id="a7d3d-163">1. SendMail.cs：主要活動的執行</span><span class="sxs-lookup"><span data-stu-id="a7d3d-163">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="a7d3d-164">SendMailDesigner 和 SendMailDesigner.xaml.cs： SendMail 活動的設計工具</span><span class="sxs-lookup"><span data-stu-id="a7d3d-164">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="a7d3d-165">3. MailTemplateBody.htm：要送出之電子郵件的範本。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-165">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="a7d3d-166">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="a7d3d-166">SendMailTestClient</span></span>|<span data-ttu-id="a7d3d-167">測試 SendMail 活動的用戶端。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-167">Client to test the SendMail activity.</span></span>  <span data-ttu-id="a7d3d-168">此專案會示範兩個方式來叫用 SendMail 活動：宣告方式和程式設計方式。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-168">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="a7d3d-169">Sequence1：調用 SendMail 活動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-169">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="a7d3d-170">2. Program.cs：叫用 Sequence1，也會以程式設計方式使用 SendMail 來建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-170">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="a7d3d-171">SendMail 活動的進一步組態設定</span><span class="sxs-lookup"><span data-stu-id="a7d3d-171">Further configuration of the SendMail activity</span></span>  

 <span data-ttu-id="a7d3d-172">使用者可以執行 SendMail 活動的進一步組態設定，但是本範例並未顯示這個部分。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-172">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="a7d3d-173">以下三節將示範如何進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-173">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="a7d3d-174">使用本文內指定的語彙基元傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="a7d3d-174">Sending an email using tokens specified in the body</span></span>  

 <span data-ttu-id="a7d3d-175">此程式碼片段會示範如何使用本文的語彙基元來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-175">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="a7d3d-176">請注意本文屬性內是如何提供語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-176">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="a7d3d-177">這些語彙基元的值會提供給語彙基元屬性。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-177">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="a7d3d-178">使用範本傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="a7d3d-178">Sending an email using a template</span></span>  

 <span data-ttu-id="a7d3d-179">此程式碼片段會示範如何使用本文的範本語彙基元來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-179">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="a7d3d-180">請注意，當設定 `BodyTemplateFilePath` 屬性時，我們不需要為 Body 屬性提供值 (範本檔案的內容將會複製到本文)。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-180">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="a7d3d-181">在測試模式下傳送郵件</span><span class="sxs-lookup"><span data-stu-id="a7d3d-181">Sending Mails in Testing Mode</span></span>  

 <span data-ttu-id="a7d3d-182">此程式碼片段示範如何設定這兩個測試屬性：將設定 `TestMailTo` 為 [所有訊息] 將傳送至 `john.doe@contoso.con` (，而不考慮 [收件者]、[副本]、[密件副本]) 的值。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-182">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="a7d3d-183">設定 TestDropPath 之後，所有外送的電子郵件也會記錄在提供的路徑上。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-183">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="a7d3d-184">這些屬性可以獨立設定 (屬性之間並沒有相關性)。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-184">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="a7d3d-185">設定指示</span><span class="sxs-lookup"><span data-stu-id="a7d3d-185">Set-Up Instructions</span></span>  

 <span data-ttu-id="a7d3d-186">這個範例需要 SMTP 伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-186">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="a7d3d-187">如需設定 SMTP 伺服器的詳細資訊，請參閱下列連結。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-187">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="a7d3d-188">[設定 SMTP 服務 (IIS 6.0) (英文)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="a7d3d-188">[Configuring the SMTP Service (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="a7d3d-189">[IIS 7.0：設定 SMTP 電子郵件](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="a7d3d-189">[IIS 7.0: Configure SMTP E-Mail](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="a7d3d-190">[如何安裝 SMTP 服務](/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="a7d3d-190">[How to Install the SMTP Service](/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="a7d3d-191">協力廠商提供的 SMTP 模擬器可供您下載。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-191">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="a7d3d-192">執行此範例</span><span class="sxs-lookup"><span data-stu-id="a7d3d-192">To run this sample</span></span>  
  
1. <span data-ttu-id="a7d3d-193">使用 Visual Studio 2010，開啟 [SendMail] 方案檔。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-193">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="a7d3d-194">確定您可以存取有效的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-194">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="a7d3d-195">請參閱設定指示。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-195">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="a7d3d-196">使用您的伺服器位址，以及從和傳送電子郵件地址來設定程式。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-196">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="a7d3d-197">若要正確執行此範例，您可能需要將的值設定為 [寄件者] 和 [寄件者] 的電子郵件地址和 SMTP 伺服器位址，並依序 Program.cs 和。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-197">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="a7d3d-198">您需要在這兩個位置中變更地址，因為此程式會以兩個不同的方式傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-198">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="a7d3d-199">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-199">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="a7d3d-200">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-200">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a7d3d-201">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-201">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7d3d-202">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a7d3d-203">如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7d3d-204">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a7d3d-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
