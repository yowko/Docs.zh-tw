---
title: "變更命名空間前置詞屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ce6e4b705188b9c1d0949703991633e3f450689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="6a0c2-102">變更命名空間前置詞屬性</span><span class="sxs-lookup"><span data-stu-id="6a0c2-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="6a0c2-103">**XmlNode**類別可讓您變更與指定之節點相關聯的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="6a0c2-104">例如，下列程式碼顯示要變更之項目的前置詞。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="6a0c2-105">**輸出**</span><span class="sxs-lookup"><span data-stu-id="6a0c2-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="6a0c2-106">變更節點的前置詞並不會變更其命名空間。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="6a0c2-107">只有在節點建立時才能設定命名空間。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="6a0c2-108">當您保留樹狀結構時，新命名空間屬性會保留以滿足您所設定的前置詞。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="6a0c2-109">如果無法建立新的命名空間，則前置詞會變更，如此節點會保留它的區域名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="6a0c2-110">下列範例顯示要加入的命名空間屬性。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="6a0c2-111">**輸出**</span><span class="sxs-lookup"><span data-stu-id="6a0c2-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="6a0c2-112">樹狀結構時要呼叫的結果為字串保留**文件。InnerXml**、`xmlns:a='123'`屬性已保留的命名空間加入`test`項目。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="6a0c2-113">它原本是 `'123'`，且仍保留為 `'123'`。</span><span class="sxs-lookup"><span data-stu-id="6a0c2-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0c2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a0c2-114">See Also</span></span>  
 [<span data-ttu-id="6a0c2-115">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="6a0c2-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
