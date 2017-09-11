---
title: "風險降低：XML 結構描述驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 786e2d0d70aaead6d464d262ca43dade8db64a52
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="76891-102">風險降低：XML 結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="76891-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="76891-103">在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中，若使用的複合索引鍵中有一個索引鍵是空的，則 XSD 結構描述驗證會偵測到唯一條件約束違規。</span><span class="sxs-lookup"><span data-stu-id="76891-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="76891-104">影響</span><span class="sxs-lookup"><span data-stu-id="76891-104">Impact</span></span>  
 <span data-ttu-id="76891-105">此變更的影響很小：根據結構描述規格的規定，因使用內含空白索引鍵的複合索引鍵而造成 `xsd:unique` 違規時，會出現結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="76891-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="76891-106">緩和</span><span class="sxs-lookup"><span data-stu-id="76891-106">Mitigation</span></span>  
 <span data-ttu-id="76891-107">當複合索引鍵包含一個空白索引鍵時，可設定是否要偵測結構描述驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="76891-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
-   <span data-ttu-id="76891-108">自目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式開始，預設值為啟用結構描述驗證錯誤偵測；但您也可以選擇不使用，如此便不會偵測結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="76891-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
-   <span data-ttu-id="76891-109">若應用程式是在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 上執行，但目標為 [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 及更舊版，預設值為不偵測結構描述驗證錯誤；但您也可以選擇使用此功能，以偵測結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="76891-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="76891-110">您可以使用 <xref:System.AppContext> 類別定義 `System.Xml.IgnoreEmptyKeySequences` 參數值，以設定此行為。</span><span class="sxs-lookup"><span data-stu-id="76891-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="76891-111">由於參數的預設值是 `false` (不忽略空的索引鍵序列)，因此您可以使用下列程式碼，將參數值設為 `true`，讓目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式不使用這項行為：</span><span class="sxs-lookup"><span data-stu-id="76891-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 <span data-ttu-id="76891-112">[!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)] [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="76891-112">[!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)] [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]</span></span>  
  
 <span data-ttu-id="76891-113">對於目標為 [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 及舊版的應用程式，因為參數預設值為 `true` (會忽略空的索引鍵序列)，所以您可以使用下列程式碼，將參數值設為 `false`，以確保包含空白索引鍵的複合索引鍵，不會產生結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="76891-113">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 <span data-ttu-id="76891-114">[!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)] [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="76891-114">[!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)] [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76891-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76891-115">See Also</span></span>  
 [<span data-ttu-id="76891-116">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="76891-116">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

