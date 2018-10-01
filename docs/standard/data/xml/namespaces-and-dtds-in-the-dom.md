---
title: DOM 中的命名空間和 DTD
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47203091"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="34505-102">DOM 中的命名空間和 DTD</span><span class="sxs-lookup"><span data-stu-id="34505-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="34505-103">文件類型定義 (DTD) 會使命名空間支援較為複雜。</span><span class="sxs-lookup"><span data-stu-id="34505-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="34505-104">例如，下列 XML 包含名稱中有冒號的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="34505-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="34505-105">如果允許此建構，下列是可能的解析：</span><span class="sxs-lookup"><span data-stu-id="34505-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
-   <span data-ttu-id="34505-106">`x:` 會被視為命名空間前置詞，但是此前置詞必須能夠使用 `xmlns:x` 命名空間宣告加以解析，此宣告也必須存在於 DTD 中。</span><span class="sxs-lookup"><span data-stu-id="34505-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="34505-107">將此前置詞對應於不同於執行個體文件中的東西會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="34505-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
-   <span data-ttu-id="34505-108">`x:` 會被視為命名空間前置詞，但是此前置詞一定要在執行個體項目的內容中進行解析。</span><span class="sxs-lookup"><span data-stu-id="34505-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="34505-109">這表示前置詞事實上可以對應於不同的命名空間統一資源識別元 (URI)，視 `item` 項目出現的命名空間範圍而定。</span><span class="sxs-lookup"><span data-stu-id="34505-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="34505-110">這項行為會比先前的項目符號中給定的解析更容易預測，但它還有其他複雜的細節，因為它要求預設屬性必須實體化。</span><span class="sxs-lookup"><span data-stu-id="34505-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
-   <span data-ttu-id="34505-111">冒號會被忽略，因為它位於 DTD 中，且屬性名稱為 `x:y`，沒有前置詞，也沒有命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="34505-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
-   <span data-ttu-id="34505-112">預設屬性中的冒號會擲回例外狀況，指出在 DTD 內不支援名稱中的冒號。</span><span class="sxs-lookup"><span data-stu-id="34505-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="34505-113">如此將可產生可預期的行為，但也表示有許多全球資訊網協會 (W3C) 所發行的 DTD 無法讓您載入。</span><span class="sxs-lookup"><span data-stu-id="34505-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
-   <span data-ttu-id="34505-114">當使用者要求 DTD 驗證時，整份文件的命名空間支援會關閉。</span><span class="sxs-lookup"><span data-stu-id="34505-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="34505-115">這樣可以載入 W3C DTD，並且產生可預期的行為。</span><span class="sxs-lookup"><span data-stu-id="34505-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="34505-116">Microsoft .NET Framework 中的 XML 可實作第二個選項以達到最大 W3C 相容性。</span><span class="sxs-lookup"><span data-stu-id="34505-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34505-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34505-117">See also</span></span>

- [<span data-ttu-id="34505-118">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="34505-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
