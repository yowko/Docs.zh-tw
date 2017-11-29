---
title: "必須是初始設定式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords: BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46ff91ec240212571f7ec9f26e82d9d128263545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="initializer-expected"></a><span data-ttu-id="a3451-102">必須是初始設定式</span><span class="sxs-lookup"><span data-stu-id="a3451-102">Initializer expected</span></span>
<span data-ttu-id="a3451-103">您嘗試使用物件初始設定式中的初始設定清單是空的如下列範例所示，宣告類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3451-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="a3451-104">至少一個欄位或屬性必須在初始設定式清單中，初始化，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a3451-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="a3451-105">**錯誤 ID:** BC30996</span><span class="sxs-lookup"><span data-stu-id="a3451-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a3451-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a3451-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a3451-107">初始化至少一個欄位或屬性初始設定式，或請勿使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="a3451-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3451-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3451-108">See Also</span></span>  
 [<span data-ttu-id="a3451-109">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="a3451-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="a3451-110">如何：使用物件初始設定式宣告物件</span><span class="sxs-lookup"><span data-stu-id="a3451-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
