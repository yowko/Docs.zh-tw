---
title: 結構 '<structurename>' 至少必須包含一個執行個體成員變數，或者至少要有一個執行個體事件宣告未標記為 'Custom'
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 4e7ef82659c43be08ee444eaf3f4df663f7aaa53
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159647"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="872ee-102">BC30941：結構 ' \<structurename> ' 必須至少包含一個實例成員變數或至少一個實例事件宣告未標記為 ' Custom '</span><span class="sxs-lookup"><span data-stu-id="872ee-102">BC30941: Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>

<span data-ttu-id="872ee-103">結構定義不包含任何非共用變數或非共用的 noncustom 事件。</span><span class="sxs-lookup"><span data-stu-id="872ee-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>

 <span data-ttu-id="872ee-104">每個結構都必須有變數或套用至每個特定實例的事件 (非共用的) ，而不是 ([共用](../modifiers/shared.md)) 共同的所有實例。</span><span class="sxs-lookup"><span data-stu-id="872ee-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="872ee-105">非共用的常數、屬性和程式不符合這項需求。</span><span class="sxs-lookup"><span data-stu-id="872ee-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="872ee-106">此外，如果沒有非共用的變數，而且只有一個非共用的事件，該事件就不能是 `Custom` 事件。</span><span class="sxs-lookup"><span data-stu-id="872ee-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>

 <span data-ttu-id="872ee-107">**錯誤識別碼：** BC30941</span><span class="sxs-lookup"><span data-stu-id="872ee-107">**Error ID:** BC30941</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="872ee-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="872ee-108">To correct this error</span></span>

- <span data-ttu-id="872ee-109">至少定義一個不是的變數或事件 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="872ee-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="872ee-110">如果您只定義一個事件，它必須是 noncustom 以及非共用的。</span><span class="sxs-lookup"><span data-stu-id="872ee-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>

## <a name="see-also"></a><span data-ttu-id="872ee-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="872ee-111">See also</span></span>

- [<span data-ttu-id="872ee-112">結構</span><span class="sxs-lookup"><span data-stu-id="872ee-112">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="872ee-113">作法：宣告結構</span><span class="sxs-lookup"><span data-stu-id="872ee-113">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="872ee-114">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="872ee-114">Structure Statement</span></span>](../statements/structure-statement.md)
