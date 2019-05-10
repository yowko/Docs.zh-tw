---
title: 陣列界限的宣告不可以出現在類型規範中
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 50e1cd0e41da467a9e816c8e5d64d09a36923d65
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665740"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="cb730-102">陣列界限的宣告不可以出現在類型規範中</span><span class="sxs-lookup"><span data-stu-id="cb730-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="cb730-103">陣列大小不可以宣告的資料類型指定名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="cb730-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="cb730-104">**錯誤 ID:** BC30638</span><span class="sxs-lookup"><span data-stu-id="cb730-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb730-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cb730-105">To correct this error</span></span>  
  
- <span data-ttu-id="cb730-106">指定陣列緊接在變數的名稱，而不是將陣列大小放在型別之後, 在下列範例所示的大小。</span><span class="sxs-lookup"><span data-stu-id="cb730-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
- <span data-ttu-id="cb730-107">定義陣列，並將它與所需數目的項目，初始化，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cb730-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cb730-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb730-108">See also</span></span>

- [<span data-ttu-id="cb730-109">陣列</span><span class="sxs-lookup"><span data-stu-id="cb730-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
