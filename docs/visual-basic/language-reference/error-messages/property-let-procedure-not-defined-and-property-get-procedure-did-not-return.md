---
title: 未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: cbd89efd144844c7b4f6264f0b6077cfab2029e2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830652"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="36c67-102">未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件</span><span class="sxs-lookup"><span data-stu-id="36c67-102">Property let procedure not defined and property get procedure did not return an object</span></span>
<span data-ttu-id="36c67-103">特定屬性、 方法和作業只能套用至`Collection`物件。</span><span class="sxs-lookup"><span data-stu-id="36c67-103">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="36c67-104">您指定的作業或是專為集合的屬性，但該物件不是集合。</span><span class="sxs-lookup"><span data-stu-id="36c67-104">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36c67-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="36c67-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="36c67-106">物件或屬性名稱的拼字檢查或確認物件是否`Collection`物件。</span><span class="sxs-lookup"><span data-stu-id="36c67-106">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2.  <span data-ttu-id="36c67-107">看看`Add`方法用來將物件加入至集合，以便能確定語法是否正確，以及任何識別項的拼字是否正確。</span><span class="sxs-lookup"><span data-stu-id="36c67-107">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c67-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36c67-108">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
