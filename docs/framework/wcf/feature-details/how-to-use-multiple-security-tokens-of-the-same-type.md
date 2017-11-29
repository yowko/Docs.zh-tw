---
title: "HOW TO：使用相同類型的多個安全性權杖"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9827d43ba4b0693d16380d93b066948d464bb978
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="34f5d-102">HOW TO：使用相同類型的多個安全性權杖</span><span class="sxs-lookup"><span data-stu-id="34f5d-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="34f5d-103">在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 中，用戶端訊息只包含任何指定類型的一個權杖。</span><span class="sxs-lookup"><span data-stu-id="34f5d-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="34f5d-104">現在，用戶端訊息可以包含某個類型的多個權杖。</span><span class="sxs-lookup"><span data-stu-id="34f5d-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="34f5d-105">本主題說明如何在用戶端訊息中包含相同類型的多個權杖。</span><span class="sxs-lookup"><span data-stu-id="34f5d-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="34f5d-106">請注意，設定服務時，服務絕對不可以只包含一個支援權杖。</span><span class="sxs-lookup"><span data-stu-id="34f5d-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="34f5d-107">使用相同類型的多個安全性權杖</span><span class="sxs-lookup"><span data-stu-id="34f5d-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="34f5d-108">建立要填入的空白繫結項目集合。</span><span class="sxs-lookup"><span data-stu-id="34f5d-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="34f5d-109">透過呼叫 <xref:System.ServiceModel.Channels.SecurityBindingElement> 建立 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>。</span><span class="sxs-lookup"><span data-stu-id="34f5d-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="34f5d-110">建立 <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> 集合。</span><span class="sxs-lookup"><span data-stu-id="34f5d-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="34f5d-111">將 SAML 權杖加入至集合。</span><span class="sxs-lookup"><span data-stu-id="34f5d-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="34f5d-112">將集合加入至 <xref:System.ServiceModel.Channels.SecurityBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="34f5d-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="34f5d-113">將繫結項目加入至繫結項目集合。</span><span class="sxs-lookup"><span data-stu-id="34f5d-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="34f5d-114">從繫結項目集合傳回建立的新自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="34f5d-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="34f5d-115">範例</span><span class="sxs-lookup"><span data-stu-id="34f5d-115">Example</span></span>  
 <span data-ttu-id="34f5d-116">下列是先前程序所述的完整方法。</span><span class="sxs-lookup"><span data-stu-id="34f5d-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="34f5d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34f5d-117">See Also</span></span>  
 [<span data-ttu-id="34f5d-118">安全性架構</span><span class="sxs-lookup"><span data-stu-id="34f5d-118">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
