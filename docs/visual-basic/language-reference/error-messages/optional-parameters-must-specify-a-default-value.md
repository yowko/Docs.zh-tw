---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: eb782b2fa1fb73c7407b57a0942e5eebb30474ff
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040933"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="b80ee-102">選擇性參數必須指定預設值</span><span class="sxs-lookup"><span data-stu-id="b80ee-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="b80ee-103">選擇性參數必須提供呼叫程式未提供參數時，可以使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="b80ee-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="b80ee-104">**錯誤識別碼：** BC30812</span><span class="sxs-lookup"><span data-stu-id="b80ee-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="b80ee-105">範例</span><span class="sxs-lookup"><span data-stu-id="b80ee-105">Example</span></span>

<span data-ttu-id="b80ee-106">下列範例會產生 BC30812：</span><span class="sxs-lookup"><span data-stu-id="b80ee-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="b80ee-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b80ee-107">To correct this error</span></span>

<span data-ttu-id="b80ee-108">指定選擇性參數的預設值：</span><span class="sxs-lookup"><span data-stu-id="b80ee-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="b80ee-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="b80ee-109">See also</span></span>

- [<span data-ttu-id="b80ee-110">Optional</span><span class="sxs-lookup"><span data-stu-id="b80ee-110">Optional</span></span>](../modifiers/optional.md)
