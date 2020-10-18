---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 3718fe5c42c8af0948f3b5cb0d120c6876c6f98f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162449"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="53e98-102">BC30812：選擇性參數必須指定預設值</span><span class="sxs-lookup"><span data-stu-id="53e98-102">BC30812: Optional parameters must specify a default value</span></span>

<span data-ttu-id="53e98-103">如果呼叫程式未提供任何參數，則選擇性參數必須提供可使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="53e98-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="53e98-104">**錯誤識別碼：** BC30812</span><span class="sxs-lookup"><span data-stu-id="53e98-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="53e98-105">範例</span><span class="sxs-lookup"><span data-stu-id="53e98-105">Example</span></span>

<span data-ttu-id="53e98-106">下列範例會產生 BC30812：</span><span class="sxs-lookup"><span data-stu-id="53e98-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="53e98-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="53e98-107">To correct this error</span></span>

<span data-ttu-id="53e98-108">指定選擇性參數的預設值：</span><span class="sxs-lookup"><span data-stu-id="53e98-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="53e98-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53e98-109">See also</span></span>

- [<span data-ttu-id="53e98-110">選擇性</span><span class="sxs-lookup"><span data-stu-id="53e98-110">Optional</span></span>](../modifiers/optional.md)
