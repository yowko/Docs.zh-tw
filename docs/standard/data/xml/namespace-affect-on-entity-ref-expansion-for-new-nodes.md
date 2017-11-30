---
title: "命名空間對包含項目和屬性的新節點之實體參考擴充的影響"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39110a9b44e6efbe7ad0331cfdb4fbe6078e7cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>命名空間對包含項目和屬性的新節點之實體參考擴充的影響
因為實體宣告的內容幾乎可包含任何內容，所以內容所包含的項目可能包括 `<!ENTITY aname "<elem>test</elem>">`。  
  
 剖析 XML 時，`&aname;` 在剖析期間不會以其取代內容進行擴充。 因為項目的命名空間解析不會發生，所以 XML 不會擴充，除非節點置於文件中。 此時才會知道範圍內的命名空間是什麼。 當節點置於文件中時，會進行命名空間解析，而且產生的實體內容會剖析進它的適當節點。  
  
> [!NOTE]
>  一旦擴充發生在新建的實體參考節點上，它就不會再發生了。 因此，項目的取代文字中所使用的命名空間會在設定父節點時產生繫結。 不過，命名空間可以變更現有實體參考節點，當您移除並插入其他地方，或者針對與所複製的實體參考節點**CloneNode**方法。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
