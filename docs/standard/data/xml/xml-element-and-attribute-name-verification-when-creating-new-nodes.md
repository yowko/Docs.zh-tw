---
title: 建立新節點時 XML 項目和屬性名稱的驗證
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 0678f7daf5276a905ce890a5f6a0f64993fb08b0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828813"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="e07ec-102">建立新節點時 XML 項目和屬性名稱的驗證</span><span class="sxs-lookup"><span data-stu-id="e07ec-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="e07ec-103">XML 文件物件模型 (DOM) 在建立新項目節點或屬性節點時會檢查名稱的有效性。</span><span class="sxs-lookup"><span data-stu-id="e07ec-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="e07ec-104">如果名稱包含不合法字元，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e07ec-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="e07ec-105">若要確保名稱是有效的且被正確編碼，您必須使用 **XmlConvert** 類別在應用程式層級來編碼名稱並且將它解碼。</span><span class="sxs-lookup"><span data-stu-id="e07ec-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="e07ec-106">**XmlWriter** 有方法來執行其他工作，以確保會產生格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="e07ec-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07ec-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="e07ec-107">See also</span></span>

- [<span data-ttu-id="e07ec-108">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="e07ec-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
