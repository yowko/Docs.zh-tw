---
title: 風險降低：XML 結構描述驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f53a2e8684029c0d1329d29a88bd1788e62d43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789674"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="a615b-102">風險降低：XML 結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="a615b-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="a615b-103">在 .NET Framework 4.6 中，如果使用複合索引鍵且其中一個索引鍵是空的，則 XSD 結構描述驗證會偵測出唯一條件約束違規。</span><span class="sxs-lookup"><span data-stu-id="a615b-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a615b-104">影響</span><span class="sxs-lookup"><span data-stu-id="a615b-104">Impact</span></span>  
 <span data-ttu-id="a615b-105">此變更的影響很小：根據結構描述規格的規定，因使用內含空白索引鍵的複合索引鍵而造成 `xsd:unique` 違規時，會出現結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a615b-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a615b-106">緩和</span><span class="sxs-lookup"><span data-stu-id="a615b-106">Mitigation</span></span>  
 <span data-ttu-id="a615b-107">當複合索引鍵包含一個空白索引鍵時，可設定是否要偵測結構描述驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="a615b-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="a615b-108">自目標為 .NET Framework 4.6 的應用程式開始，預設值為啟用結構描述驗證錯誤偵測；但您也可以選擇不使用，如此便不會偵測結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a615b-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="a615b-109">若應用程式是在 .NET Framework 4.6 上執行，但目標為 .NET Framework 4.5.2 及更舊版，則預設為不偵測結構描述驗證錯誤；但您也可以選擇使用此功能，以偵測結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a615b-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="a615b-110">您可以使用 <xref:System.AppContext> 類別定義 `System.Xml.IgnoreEmptyKeySequences` 參數值，以設定此行為。</span><span class="sxs-lookup"><span data-stu-id="a615b-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="a615b-111">由於參數的預設值是 `false` (不忽略空的索引鍵序列)，因此您可以使用下列程式碼，將參數值設為 `true`，讓目標為 NET Framework 4.6 的應用程式不使用這項行為：</span><span class="sxs-lookup"><span data-stu-id="a615b-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="a615b-112">對於目標為 .NET Framework 4.5.2 及舊版的應用程式，因為參數預設值為 `true` (會忽略空的索引鍵序列)，所以您可以使用下列程式碼，將參數值設為 `false`，以確保包含空白索引鍵的複合索引鍵不會產生結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a615b-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a615b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a615b-113">See also</span></span>

- [<span data-ttu-id="a615b-114">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="a615b-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
