---
title: 未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871093"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="474f5-102">未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件</span><span class="sxs-lookup"><span data-stu-id="474f5-102">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="474f5-103">某些屬性、方法和作業只能套用至 `Collection` 物件。</span><span class="sxs-lookup"><span data-stu-id="474f5-103">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="474f5-104">您指定了集合專屬的作業或屬性，但物件不是集合。</span><span class="sxs-lookup"><span data-stu-id="474f5-104">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="474f5-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="474f5-105">To correct this error</span></span>  
  
1. <span data-ttu-id="474f5-106">檢查物件或屬性名稱的拼寫，或確認物件是 `Collection` 物件。</span><span class="sxs-lookup"><span data-stu-id="474f5-106">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="474f5-107">查看 `Add` 用來將物件加入至集合的方法，以確定語法正確，且任何識別碼拼寫正確。</span><span class="sxs-lookup"><span data-stu-id="474f5-107">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="474f5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="474f5-108">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
