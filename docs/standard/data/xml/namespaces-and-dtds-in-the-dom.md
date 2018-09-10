---
title: DOM 中的命名空間和 DTD
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177415"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>DOM 中的命名空間和 DTD
文件類型定義 (DTD) 會使命名空間支援較為複雜。 例如，下列 XML 包含名稱中有冒號的預設屬性。  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 如果允許此建構，下列是可能的解析：  
  
-   `x:` 會被視為命名空間前置詞，但是此前置詞必須能夠使用 `xmlns:x` 命名空間宣告加以解析，此宣告也必須存在於 DTD 中。 將此前置詞對應於不同於執行個體文件中的東西會發生錯誤。  
  
-   `x:` 會被視為命名空間前置詞，但是此前置詞一定要在執行個體項目的內容中進行解析。 這表示前置詞事實上可以對應於不同的命名空間統一資源識別元 (URI)，視 `item` 項目出現的命名空間範圍而定。 這項行為會比先前的項目符號中給定的解析更容易預測，但它還有其他複雜的細節，因為它要求預設屬性必須實體化。  
  
-   冒號會被忽略，因為它位於 DTD 中，且屬性名稱為 `x:y`，沒有前置詞，也沒有命名空間 URI。  
  
-   預設屬性中的冒號會擲回例外狀況，指出在 DTD 內不支援名稱中的冒號。 如此將可產生可預期的行為，但也表示有許多全球資訊網協會 (W3C) 所發行的 DTD 無法讓您載入。  
  
-   當使用者要求 DTD 驗證時，整份文件的命名空間支援會關閉。 這樣可以載入 W3C DTD，並且產生可預期的行為。  
  
 Microsoft .NET Framework 中的 XML 可實作第二個選項以達到最大 W3C 相容性。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
