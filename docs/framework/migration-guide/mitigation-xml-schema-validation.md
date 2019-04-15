---
title: 風險降低：XML 結構描述驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5c0087412a53177a7c43df838266f6d896c1bd9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220470"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="24165-102">風險降低：XML 結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="24165-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="24165-103">在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中，若使用的複合索引鍵中有一個索引鍵是空的，則 XSD 結構描述驗證會偵測到唯一條件約束違規。</span><span class="sxs-lookup"><span data-stu-id="24165-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="24165-104">影響</span><span class="sxs-lookup"><span data-stu-id="24165-104">Impact</span></span>  
 <span data-ttu-id="24165-105">此變更的影響很小：根據結構描述規格的規定，因使用內含空白索引鍵的複合索引鍵而造成 `xsd:unique` 違規時，會出現結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="24165-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="24165-106">緩和</span><span class="sxs-lookup"><span data-stu-id="24165-106">Mitigation</span></span>  
 <span data-ttu-id="24165-107">當複合索引鍵包含一個空白索引鍵時，可設定是否要偵測結構描述驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="24165-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
-   <span data-ttu-id="24165-108">自目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式開始，預設值為啟用結構描述驗證錯誤偵測；但您也可以選擇不使用，如此便不會偵測結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="24165-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
-   <span data-ttu-id="24165-109">若應用程式是在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 上執行，但目標為 [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 及更舊版，預設值為不偵測結構描述驗證錯誤；但您也可以選擇使用此功能，以偵測結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="24165-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="24165-110">您可以使用 <xref:System.AppContext> 類別定義 `System.Xml.IgnoreEmptyKeySequences` 參數值，以設定此行為。</span><span class="sxs-lookup"><span data-stu-id="24165-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="24165-111">由於參數的預設值是 `false` (不忽略空的索引鍵序列)，因此您可以使用下列程式碼，將參數值設為 `true`，讓目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式不使用這項行為：</span><span class="sxs-lookup"><span data-stu-id="24165-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="24165-112">對於目標為 [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 及舊版的應用程式，因為參數預設值為 `true` (會忽略空的索引鍵序列)，所以您可以使用下列程式碼，將參數值設為 `false`，以確保包含空白索引鍵的複合索引鍵，不會產生結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="24165-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="24165-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24165-113">See also</span></span>

- [<span data-ttu-id="24165-114">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="24165-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
