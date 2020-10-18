---
title: 共用 WithEvents 變數的事件不能由非共用的方法處理
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 02039b81251e59a951a0fe37ec2c9534b458b6a5
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161916"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="3837b-102">BC30594：共用 WithEvents 變數的事件不能由非共用的方法處理</span><span class="sxs-lookup"><span data-stu-id="3837b-102">BC30594: Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>

<span data-ttu-id="3837b-103">使用修飾詞宣告的變數 `Shared` 是共用變數。</span><span class="sxs-lookup"><span data-stu-id="3837b-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="3837b-104">共用變數只會識別一個儲存位置。</span><span class="sxs-lookup"><span data-stu-id="3837b-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="3837b-105">以修飾詞宣告的變數會判斷提示 `WithEvents` 所屬的類型會處理變數所引發的事件集。</span><span class="sxs-lookup"><span data-stu-id="3837b-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="3837b-106">將值指派給變數時，宣告所建立的屬性會解除 `WithEvents` 所有現有的事件處理常式的連結，並透過方法連結新的事件處理常式 `Add` 。</span><span class="sxs-lookup"><span data-stu-id="3837b-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>

 <span data-ttu-id="3837b-107">**錯誤識別碼：** BC30594</span><span class="sxs-lookup"><span data-stu-id="3837b-107">**Error ID:** BC30594</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3837b-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3837b-108">To correct this error</span></span>

- <span data-ttu-id="3837b-109">宣告您的事件處理常式 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="3837b-109">Declare your event handler `Shared`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3837b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3837b-110">See also</span></span>

- <span data-ttu-id="3837b-111">[共用][](../modifiers/shared.md)</span><span class="sxs-lookup"><span data-stu-id="3837b-111">[Shared](../modifiers/shared.md)</span></span>
- [<span data-ttu-id="3837b-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="3837b-112">WithEvents</span></span>](../modifiers/withevents.md)
