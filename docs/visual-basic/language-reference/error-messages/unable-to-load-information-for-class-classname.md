---
title: 無法載入類別 '<classname>' 的資訊
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 05c3303db90a396479bc396c5c2395c3afbb59ae
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161604"
---
# <a name="bc30712-unable-to-load-information-for-class-classname"></a><span data-ttu-id="f25ac-102">BC30712：無法載入類別 ' ' 的資訊 \<classname></span><span class="sxs-lookup"><span data-stu-id="f25ac-102">BC30712: Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="f25ac-103">對無法使用的類別進行參考。</span><span class="sxs-lookup"><span data-stu-id="f25ac-103">A reference was made to a class that is not available.</span></span>

 <span data-ttu-id="f25ac-104">**錯誤識別碼：** BC30712</span><span class="sxs-lookup"><span data-stu-id="f25ac-104">**Error ID:** BC30712</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f25ac-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f25ac-105">To correct this error</span></span>

1. <span data-ttu-id="f25ac-106">確認類別已定義，而且您的名稱拼寫正確。</span><span class="sxs-lookup"><span data-stu-id="f25ac-106">Verify that the class is defined and that you spelled the name correctly.</span></span>

2. <span data-ttu-id="f25ac-107">嘗試存取模組中所宣告的其中一個成員。</span><span class="sxs-lookup"><span data-stu-id="f25ac-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="f25ac-108">在某些情況下，偵錯環境找不到成員，因為尚未載入宣告它們的模組。</span><span class="sxs-lookup"><span data-stu-id="f25ac-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>

## <a name="see-also"></a><span data-ttu-id="f25ac-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f25ac-109">See also</span></span>

- [<span data-ttu-id="f25ac-110">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="f25ac-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
