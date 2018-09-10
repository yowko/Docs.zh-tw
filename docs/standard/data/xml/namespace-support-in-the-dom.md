---
title: DOM 中支援的命名空間
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcc796f8d895e3daa81a9607bd7c4941b747cf24
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44208766"
---
# <a name="namespace-support-in-the-dom"></a>DOM 中支援的命名空間
XML 文件物件模型 (DOM) 具有完全的命名空間感知。 只有命名空間感知 XML 文件受支援。 全球資訊網協會 (W3C) 指定實作層級 1 的 DOM 應用程式可不具備命名空間感知，而 DOM 層級 2 功能則具有命名空間感知。 然而，不論方法是來自層級 1 或層級 2 DOM 建議事項，XML DOM 中所有的功能都具有命名空間感知。  
  
 例如，若在非命名空間設定中呼叫 `setAttribute("A:b", "123")` (根據 DOM 層級 1 建議事項中所指定)，並不會產生具有前置詞 `A` 和區域名稱 `b` 的屬性。 它會產生具有值 `A:b` 的屬性。  
  
 若在具有命名空間感知的環境中呼叫 DOM 層級 2 `setAttribute("A:b", "123")`，則會產生具有前置詞 `A` 和區域名稱 `b` 的屬性。 這就是 Microsoft .NET Framework DOM 的運作方式。  
  
 因此，對於所有採用名稱參數的方法，這些方法也會採用前置詞來限定名稱。 名稱參數 (例如 **setAttribute** DOM 層級 1 方法中的 `A:b`) 會以下列方式剖析：  
  
-   如果沒有冒號 (:) 字元，則區域名稱會設為 `name` 參數，而前置詞和 NamespaceURI 則為空字串。  
  
-   如果找到冒號，則名稱會根據第一個冒號字元的位置分成兩個部分。 前置詞會設為冒號之前找到的字串，而且區域名稱會設為冒號之後找到的字串。 對於沒有採用 NamespaceURI 值的方法，NamespaceURI 不會解析且會維持設定為空字串。 否則，NamespaceURI 會設為傳入方法的字串。 如果沒有指定前置詞，那麼 **Save** 方法以及 **InnerXml** 和 **OuterXml** 屬性會失敗。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
