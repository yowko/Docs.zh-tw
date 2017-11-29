---
title: "陣列界限的宣告不可以出現在類型規範中"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords: BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770f86ca960110965b6917a22d284678ff8b6f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="cb5cb-102">陣列界限的宣告不可以出現在類型規範中</span><span class="sxs-lookup"><span data-stu-id="cb5cb-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="cb5cb-103">陣列大小不可以宣告做為資料類型規範的一部分。</span><span class="sxs-lookup"><span data-stu-id="cb5cb-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="cb5cb-104">**錯誤 ID:** BC30638</span><span class="sxs-lookup"><span data-stu-id="cb5cb-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb5cb-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cb5cb-105">To correct this error</span></span>  
  
-   <span data-ttu-id="cb5cb-106">指定緊接在型別之後，而陣列大小的變數名稱在下列範例所示陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="cb5cb-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="cb5cb-107">定義陣列，並初始化與所需數目的項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cb5cb-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cb5cb-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb5cb-108">See Also</span></span>  
 [<span data-ttu-id="cb5cb-109">陣列</span><span class="sxs-lookup"><span data-stu-id="cb5cb-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
