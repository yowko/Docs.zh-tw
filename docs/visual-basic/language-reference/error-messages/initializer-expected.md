---
title: 必須是初始設定式
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 77cfeb57bc313ded2d2c4d5a0c59041c5c19f515
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826076"
---
# <a name="initializer-expected"></a><span data-ttu-id="9cfb4-102">必須是初始設定式</span><span class="sxs-lookup"><span data-stu-id="9cfb4-102">Initializer expected</span></span>
<span data-ttu-id="9cfb4-103">您嘗試使用物件初始設定式中的初始設定清單是空的如下列範例所示，宣告類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9cfb4-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="9cfb4-104">至少一個欄位或屬性必須在初始設定式清單中，初始化，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9cfb4-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="9cfb4-105">**錯誤 ID:** BC30996</span><span class="sxs-lookup"><span data-stu-id="9cfb4-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9cfb4-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9cfb4-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9cfb4-107">初始化至少一個欄位或屬性初始設定式，或不使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="9cfb4-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfb4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cfb4-108">See also</span></span>

- [<span data-ttu-id="9cfb4-109">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="9cfb4-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="9cfb4-110">如何：使用物件初始設定式宣告物件</span><span class="sxs-lookup"><span data-stu-id="9cfb4-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
