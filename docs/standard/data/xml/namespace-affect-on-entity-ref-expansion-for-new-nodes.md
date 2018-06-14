---
title: 命名空間對包含項目和屬性的新節點之實體參考擴充的影響
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2ba9964f17380e868ea5fe906a40f8b491018a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568897"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>命名空間對包含項目和屬性的新節點之實體參考擴充的影響
因為實體宣告的內容幾乎可包含任何內容，所以內容所包含的項目可能包括 `<!ENTITY aname "<elem>test</elem>">`。  
  
 剖析 XML 時，`&aname;` 在剖析期間不會以其取代內容進行擴充。 因為項目的命名空間解析不會發生，所以 XML 不會擴充，除非節點置於文件中。 此時才會知道範圍內的命名空間是什麼。 當節點置於文件中時，會進行命名空間解析，而且產生的實體內容會剖析進它的適當節點。  
  
> [!NOTE]
>  一旦擴充發生在新建的實體參考節點上，它就不會再發生了。 因此，項目的取代文字中所使用的命名空間會在設定父節點時產生繫結。 然而，在您移除命名空間並將其插入其他地方，或者在以 **CloneNode** 方法複製的實體參考節點上時，會為現有實體參考節點變更命名空間。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
