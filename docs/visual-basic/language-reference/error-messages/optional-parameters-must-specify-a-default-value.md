---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 0f501b518d5b3f2d48ced33885da2afd353c609e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665681"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="aabba-102">選擇性參數必須指定預設值</span><span class="sxs-lookup"><span data-stu-id="aabba-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="aabba-103">選擇性參數必須提供預設值，如果未提供參數呼叫程序可以使用。</span><span class="sxs-lookup"><span data-stu-id="aabba-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="aabba-104">**錯誤 ID:** BC30812</span><span class="sxs-lookup"><span data-stu-id="aabba-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aabba-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="aabba-105">To correct this error</span></span>  
  
- <span data-ttu-id="aabba-106">指定選擇性參數，預設的值例如：</span><span class="sxs-lookup"><span data-stu-id="aabba-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="aabba-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aabba-107">See also</span></span>

- [<span data-ttu-id="aabba-108">Optional</span><span class="sxs-lookup"><span data-stu-id="aabba-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
