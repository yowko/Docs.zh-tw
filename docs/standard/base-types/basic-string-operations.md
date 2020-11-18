---
title: .NET 中的基本字串作業
description: 了解您可以對字串執行的基本作業。
ms.date: 03/30/2017
helpviewer_keywords:
- strings [.NET], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 30f325a414e0912086b5d36630e77ea754db4956
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825126"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="d58b2-103">.NET 中的基底字元串作業</span><span class="sxs-lookup"><span data-stu-id="d58b2-103">Basic string operations in .NET</span></span>

<span data-ttu-id="d58b2-104">應用程式通常是以根據使用者輸入建構訊息的方式來回應使用者。</span><span class="sxs-lookup"><span data-stu-id="d58b2-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="d58b2-105">例如，網站使用包含使用者名稱的特殊問候語來回應新登入的使用者並不罕見。</span><span class="sxs-lookup"><span data-stu-id="d58b2-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="d58b2-106"><xref:System.String?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別中有數個方法，可讓您以動態方式建構要在使用者介面中顯示的自訂字串。</span><span class="sxs-lookup"><span data-stu-id="d58b2-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="d58b2-107">這些方法也可協助您執行一些基本字串作業，例如從位元組陣列建立新的字串、比較字串值，以及修改現有的字串。</span><span class="sxs-lookup"><span data-stu-id="d58b2-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d58b2-108">相關章節</span><span class="sxs-lookup"><span data-stu-id="d58b2-108">Related sections</span></span>

<span data-ttu-id="d58b2-109">[.NET 中的類型轉換](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="d58b2-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="d58b2-110">描述如何將一個類型轉換為另一個類型。</span><span class="sxs-lookup"><span data-stu-id="d58b2-110">Describes how to convert one type into another type.</span></span>

<span data-ttu-id="d58b2-111">[格式化類型](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="d58b2-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="d58b2-112">描述如何使用格式規範來將字串格式化。</span><span class="sxs-lookup"><span data-stu-id="d58b2-112">Describes how to format strings using format specifiers.</span></span>
