---
title: 巢狀函式沒有與委派 '<delegatename>' 相容的簽章
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 0dde340164f1ba80d0e1d9fbb5d17ba6da0a5bc4
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160050"
---
# <a name="bc36532-nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="12e4d-102">BC36532：嵌套函數沒有與委派 ' ' 相容的簽章 \<delegatename></span><span class="sxs-lookup"><span data-stu-id="12e4d-102">BC36532: Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>

<span data-ttu-id="12e4d-103">Lambda 運算式已指派給具有不相容簽章的委派。</span><span class="sxs-lookup"><span data-stu-id="12e4d-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="12e4d-104">例如，在下列程式碼中，委派 `Del` 有兩個整數參數。</span><span class="sxs-lookup"><span data-stu-id="12e4d-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

<span data-ttu-id="12e4d-105">如果有一個引數的 lambda 運算式宣告為類型，就會引發此錯誤 `Del` ：</span><span class="sxs-lookup"><span data-stu-id="12e4d-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

<span data-ttu-id="12e4d-106">**錯誤識別碼：** BC36532</span><span class="sxs-lookup"><span data-stu-id="12e4d-106">**Error ID:** BC36532</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="12e4d-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="12e4d-107">To correct this error</span></span>

<span data-ttu-id="12e4d-108">請調整委派定義或指派的 lambda 運算式，讓簽章相容。</span><span class="sxs-lookup"><span data-stu-id="12e4d-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>

## <a name="see-also"></a><span data-ttu-id="12e4d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12e4d-109">See also</span></span>

- [<span data-ttu-id="12e4d-110">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="12e4d-110">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="12e4d-111">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="12e4d-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
