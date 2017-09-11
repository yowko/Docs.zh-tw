---
title: "基本字串作業"
description: "基本字串作業"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9658098d-de60-4868-ba5b-0c278748a90f
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b8bdbeccd226c412e725200fcaf81ec568afc5bc
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="basic-string-operations"></a><span data-ttu-id="933ad-104">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="933ad-104">Basic string operations</span></span>

<span data-ttu-id="933ad-105">應用程式通常是以根據使用者輸入建構訊息的方式來回應使用者。</span><span class="sxs-lookup"><span data-stu-id="933ad-105">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="933ad-106">例如，網站就經常以包含使用者姓名的特殊問候語來回應新登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="933ad-106">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="933ad-107">[System.String](xref:System.String) 和 [System.Text.StringBuilder](xref:System.Text.StringBuilder) 類別中有幾個方法可讓您以動態方式建構要顯示在使用者介面中的自訂字串。</span><span class="sxs-lookup"><span data-stu-id="933ad-107">Several methods in the [System.String](xref:System.String) and [System.Text.StringBuilder](xref:System.Text.StringBuilder) classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="933ad-108">這些方法也可協助您執行一些基本字串作業，例如從位元組陣列建立新的字串、比較字串值，以及修改現有的字串。</span><span class="sxs-lookup"><span data-stu-id="933ad-108">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="933ad-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="933ad-109">In This Section</span></span>

<span data-ttu-id="933ad-110">[建立新字串](creating-new.md) - 描述將物件轉換為字串和組合字串的基本方式。</span><span class="sxs-lookup"><span data-stu-id="933ad-110">[Creating new strings](creating-new.md) - Describes basic ways to convert objects into strings and to combine strings.</span></span>

<span data-ttu-id="933ad-111">[修剪和移除字元](trimming.md) - 描述如何修剪或移除字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="933ad-111">[Trimming and removing characters](trimming.md) - Describes how to trim or remove characters in a string.</span></span> 

<span data-ttu-id="933ad-112">[填補字串](padding.md) - 描述如何將字元或空格插入字串中。</span><span class="sxs-lookup"><span data-stu-id="933ad-112">[Padding strings](padding.md) - Describes how to insert characters or empty spaces into a string.</span></span>

<span data-ttu-id="933ad-113">[比較字串](comparing.md) - 描述如何比較兩個或多個字串的內容。</span><span class="sxs-lookup"><span data-stu-id="933ad-113">[Comparing strings](comparing.md) - Describes how to compare the contents of two or more strings.</span></span>

<span data-ttu-id="933ad-114">[變更大小寫](changing-case.md) - 描述如何變更字串內的字元大小寫。</span><span class="sxs-lookup"><span data-stu-id="933ad-114">[Changing case](changing-case.md) - Describes how to change the case of characters within a string.</span></span>

<span data-ttu-id="933ad-115">[使用 StringBuilder 類別](stringbuilder.md) - 說明如何使用 [StringBuilder](xref:System.Text.StringBuilder) 類別建立和修改動態字串物件。</span><span class="sxs-lookup"><span data-stu-id="933ad-115">[Using the StringBuilder class](stringbuilder.md) - Describes how to create and modify dynamic string objects with the [StringBuilder](xref:System.Text.StringBuilder) class.</span></span>

<span data-ttu-id="933ad-116">[如何︰執行基本字串操作](basic-manipulations.md) - 示範基本字串作業的用法。</span><span class="sxs-lookup"><span data-stu-id="933ad-116">[How to: Perform basic string manipulations](basic-manipulations.md) - Demonstrates the use of basic string operations.</span></span>

## <a name="related-sections"></a><span data-ttu-id="933ad-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="933ad-117">Related Sections</span></span>

<span data-ttu-id="933ad-118">[類型轉換](type-conversion.md) - 描述如何將一個類型轉換為另一個類型。</span><span class="sxs-lookup"><span data-stu-id="933ad-118">[Type conversion](type-conversion.md) - Describes how to convert from one type to another.</span></span>

<span data-ttu-id="933ad-119">[格式化類型](formatting-types.md) - 描述如何使用格式規範來格式化字串。</span><span class="sxs-lookup"><span data-stu-id="933ad-119">[Formatting types](formatting-types.md) - Describes how to format strings using the string format specifiers.</span></span>



