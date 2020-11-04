---
title: .NET 中的基底字元串操作
description: 請參閱呼叫許多字串方法的範例。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 659f01cc1d7ae03e12e83329e4fd2446b7512475
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342614"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="7529e-103">如何：在 .NET 中執行基本字串操作</span><span class="sxs-lookup"><span data-stu-id="7529e-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="7529e-104">下列範例會使用[基本字串作業](basic-string-operations.md)主題中所討論的一些方法，以一種可能在實際應用程式中發現的方式，來建構可執行字串操作的類別。</span><span class="sxs-lookup"><span data-stu-id="7529e-104">The following example uses some of the methods discussed in the [Basic String Operations](basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="7529e-105">`MailToData` 類別會將個人的姓名和地址儲存在不同的屬性中，並允許您將 `City`、`State` 和 `Zip` 欄位組合成單一字串，以便顯示給使用者看。</span><span class="sxs-lookup"><span data-stu-id="7529e-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="7529e-106">此外，此類別可讓使用者以單一字串形式輸入 city、state 和 zip 程式碼資訊。</span><span class="sxs-lookup"><span data-stu-id="7529e-106">Furthermore, the class allows the user to enter the city, state, and zip code information as a single string.</span></span> <span data-ttu-id="7529e-107">應用程式會自動剖析單一字串，並將適當的資訊輸入到對應的屬性中。</span><span class="sxs-lookup"><span data-stu-id="7529e-107">The application automatically parses the single string and enters the proper information into the corresponding property.</span></span>

<span data-ttu-id="7529e-108">為了簡單起見，這個範例會使用具有命令列介面的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="7529e-108">For simplicity, this example uses a console application with a command-line interface.</span></span>

## <a name="example"></a><span data-ttu-id="7529e-109">範例</span><span class="sxs-lookup"><span data-stu-id="7529e-109">Example</span></span>

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]

<span data-ttu-id="7529e-110">執行上述程式碼時，系統會要求使用者輸入其名稱和位址。</span><span class="sxs-lookup"><span data-stu-id="7529e-110">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="7529e-111">應用程式會將資訊放在適當的屬性中，並向使用者顯示資訊，並建立單一字串來顯示城市、州和郵遞區號資訊。</span><span class="sxs-lookup"><span data-stu-id="7529e-111">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and zip code information.</span></span>

## <a name="see-also"></a><span data-ttu-id="7529e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7529e-112">See also</span></span>

- [<span data-ttu-id="7529e-113">基底字元串作業</span><span class="sxs-lookup"><span data-stu-id="7529e-113">Basic String Operations</span></span>](basic-string-operations.md)
