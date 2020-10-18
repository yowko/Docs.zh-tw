---
title: 呼叫 'Dir' 函式一定要有 'PathName' 引數
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 7f8191b0ef5452fcf6f3a20c3e0f28ca84ef9c4a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163424"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="b3d62-102">呼叫 'Dir' 函式一定要有 'PathName' 引數</span><span class="sxs-lookup"><span data-stu-id="b3d62-102">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="b3d62-103">函數的初始呼叫不 `Dir` 包含 `PathName` 引數。</span><span class="sxs-lookup"><span data-stu-id="b3d62-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="b3d62-104">的第一個呼叫 `Dir` 必須包含 `PathName` ，但後續呼叫 `Dir` 不需要包含參數來取出下一個專案。</span><span class="sxs-lookup"><span data-stu-id="b3d62-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b3d62-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b3d62-105">To correct this error</span></span>

- <span data-ttu-id="b3d62-106">`PathName`在函式呼叫中提供引數。</span><span class="sxs-lookup"><span data-stu-id="b3d62-106">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3d62-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3d62-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
