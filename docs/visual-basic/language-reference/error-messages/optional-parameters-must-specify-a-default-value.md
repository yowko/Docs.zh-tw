---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: b32c150f0faf4a9dcec3cec7620c3a9c050f6f20
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696876"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="4ee36-102">選擇性參數必須指定預設值</span><span class="sxs-lookup"><span data-stu-id="4ee36-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="4ee36-103">選擇性參數必須提供呼叫程式未提供參數時，可以使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="4ee36-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="4ee36-104">**錯誤識別碼：** BC30812</span><span class="sxs-lookup"><span data-stu-id="4ee36-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ee36-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4ee36-105">To correct this error</span></span>  
  
- <span data-ttu-id="4ee36-106">指定選擇性參數的預設值;例如：</span><span class="sxs-lookup"><span data-stu-id="4ee36-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```vb  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4ee36-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ee36-107">See also</span></span>

- [<span data-ttu-id="4ee36-108">Optional</span><span class="sxs-lookup"><span data-stu-id="4ee36-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
