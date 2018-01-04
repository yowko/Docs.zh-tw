---
title: "HOW TO：設定簽章確認"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53e38658671f3a36da67619c796667ecad61f286
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="15b02-102">HOW TO：設定簽章確認</span><span class="sxs-lookup"><span data-stu-id="15b02-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="15b02-103">*簽章確認*是確保收到的回覆已產生寄件者的原始訊息的回應是訊息啟動器的機制。</span><span class="sxs-lookup"><span data-stu-id="15b02-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="15b02-104">簽章確認是定義在 WS-Security 1.1 規格中。</span><span class="sxs-lookup"><span data-stu-id="15b02-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="15b02-105">如果端點支援 WS-Security 1.0，您就無法使用簽章確認。</span><span class="sxs-lookup"><span data-stu-id="15b02-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="15b02-106">下列程序會指定如何使用 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 啟用簽章確認。</span><span class="sxs-lookup"><span data-stu-id="15b02-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="15b02-107">您可以搭配 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 使用相同的程序。</span><span class="sxs-lookup"><span data-stu-id="15b02-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="15b02-108">此程序為建立基礎中找到的基本步驟[How to： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。</span><span class="sxs-lookup"><span data-stu-id="15b02-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="15b02-109">若要在程式碼中啟用簽章確認</span><span class="sxs-lookup"><span data-stu-id="15b02-109">To enable signature confirmation in code</span></span>  
  
1.  <span data-ttu-id="15b02-110">建立 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="15b02-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2.  <span data-ttu-id="15b02-111">建立的執行個體<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>類別。</span><span class="sxs-lookup"><span data-stu-id="15b02-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3.  <span data-ttu-id="15b02-112">將 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="15b02-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="15b02-113">將安全性項目新增至繫結集合中。</span><span class="sxs-lookup"><span data-stu-id="15b02-113">Add the security element to the binding collection.</span></span>  
  
5.  <span data-ttu-id="15b02-114">建立自訂繫結，如中所指定[How to： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。</span><span class="sxs-lookup"><span data-stu-id="15b02-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="15b02-115">若要在組態中啟用簽章確認</span><span class="sxs-lookup"><span data-stu-id="15b02-115">To enable signature confirmation in configuration</span></span>  
  
1.  <span data-ttu-id="15b02-116">將 `<customBinding>` 項目新增至組態檔的 `<bindings>` 區段中。</span><span class="sxs-lookup"><span data-stu-id="15b02-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="15b02-117">新增 `<binding>` 項目，並將名稱屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="15b02-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="15b02-118">新增適當的編碼項目。</span><span class="sxs-lookup"><span data-stu-id="15b02-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="15b02-119">下列範例會新增 `<TextMessageEncoding>` 項目。</span><span class="sxs-lookup"><span data-stu-id="15b02-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4.  <span data-ttu-id="15b02-120">新增 `<security>` 子項目並將 `requireSignatureConfirmation` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="15b02-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5.  <span data-ttu-id="15b02-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="15b02-121">Optional.</span></span> <span data-ttu-id="15b02-122">若要啟用期間啟動安裝程式的簽章確認，新增[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)子元素，並設定`equireSignatureConfirmation`屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="15b02-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6.  <span data-ttu-id="15b02-123">新增適當的傳輸項目。</span><span class="sxs-lookup"><span data-stu-id="15b02-123">Add an appropriate transport element.</span></span> <span data-ttu-id="15b02-124">下列範例會將[ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="15b02-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a><span data-ttu-id="15b02-125">範例</span><span class="sxs-lookup"><span data-stu-id="15b02-125">Example</span></span>  
 <span data-ttu-id="15b02-126">下列程式碼會建立 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的執行個體，並將 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="15b02-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="15b02-127">請注意，這個範例並未使用之前範例中出現的 `<secureConversationBootstrap>` 項目，</span><span class="sxs-lookup"><span data-stu-id="15b02-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="15b02-128">但會在使用 Windows (Kerberos 通訊協定) 權杖時示範簽章確認。</span><span class="sxs-lookup"><span data-stu-id="15b02-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="15b02-129">在這種情況下，來自服務的所有回應中都會傳回用戶端的簽章，並且經由用戶端確認。</span><span class="sxs-lookup"><span data-stu-id="15b02-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="15b02-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="15b02-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [<span data-ttu-id="15b02-131">如何：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="15b02-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="15b02-132">如何：為指定的驗證模式建立 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="15b02-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
