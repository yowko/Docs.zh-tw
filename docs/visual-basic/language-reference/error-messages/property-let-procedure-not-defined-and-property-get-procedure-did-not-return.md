---
title: "未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b043ca698a9c90afd41de90c7dbc5879ae7de623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="6a721-102">未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件</span><span class="sxs-lookup"><span data-stu-id="6a721-102">Property let procedure not defined and property get procedure did not return an object</span></span>
<span data-ttu-id="6a721-103">特定的屬性、 方法和作業只能套用至`Collection`物件。</span><span class="sxs-lookup"><span data-stu-id="6a721-103">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="6a721-104">您指定的作業或專屬於集合的屬性，但物件不是集合。</span><span class="sxs-lookup"><span data-stu-id="6a721-104">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a721-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6a721-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="6a721-106">請檢查拼字的物件或屬性名稱，或確認物件是`Collection`物件。</span><span class="sxs-lookup"><span data-stu-id="6a721-106">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2.  <span data-ttu-id="6a721-107">查看`Add`方法用來將物件加入至集合，以便能確定語法是否正確，以及任何識別項的拼字是否正確。</span><span class="sxs-lookup"><span data-stu-id="6a721-107">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a721-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a721-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Collection>
