---
title: HOW TO：使用相同類型的多個安全性權杖
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: e82c2e256b057f45863d0533efd0c53b921cadce
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650272"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="74df1-102">HOW TO：使用相同類型的多個安全性權杖</span><span class="sxs-lookup"><span data-stu-id="74df1-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
- <span data-ttu-id="74df1-103">在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 中，用戶端訊息只包含任何指定類型的一個權杖。</span><span class="sxs-lookup"><span data-stu-id="74df1-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="74df1-104">現在，用戶端訊息可以包含某個類型的多個權杖。</span><span class="sxs-lookup"><span data-stu-id="74df1-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="74df1-105">本主題說明如何在用戶端訊息中包含相同類型的多個權杖。</span><span class="sxs-lookup"><span data-stu-id="74df1-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="74df1-106">請注意，設定服務時，服務絕對不可以只包含一個支援權杖。</span><span class="sxs-lookup"><span data-stu-id="74df1-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="74df1-107">使用相同類型的多個安全性權杖</span><span class="sxs-lookup"><span data-stu-id="74df1-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="74df1-108">建立要填入的空白繫結項目集合。</span><span class="sxs-lookup"><span data-stu-id="74df1-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="74df1-109">透過呼叫 <xref:System.ServiceModel.Channels.SecurityBindingElement> 建立 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>。</span><span class="sxs-lookup"><span data-stu-id="74df1-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="74df1-110">建立 <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> 集合。</span><span class="sxs-lookup"><span data-stu-id="74df1-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="74df1-111">將 SAML 權杖加入至集合。</span><span class="sxs-lookup"><span data-stu-id="74df1-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="74df1-112">將集合加入至 <xref:System.ServiceModel.Channels.SecurityBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="74df1-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="74df1-113">將繫結項目加入至繫結項目集合。</span><span class="sxs-lookup"><span data-stu-id="74df1-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="74df1-114">從繫結項目集合傳回建立的新自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="74df1-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="74df1-115">範例</span><span class="sxs-lookup"><span data-stu-id="74df1-115">Example</span></span>  
 <span data-ttu-id="74df1-116">下列是先前程序所述的完整方法。</span><span class="sxs-lookup"><span data-stu-id="74df1-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
