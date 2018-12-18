---
title: .NET 中的基本字串作業
description: 了解您可以對字串執行的基本作業。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
author: rpetrusha
ms.author: ronpet
ms.custom: seadec18
ms.openlocfilehash: 8621e79ad6e305f3859dc269965ecd216081f695
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150676"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="328ea-103">.NET 中的基本字串作業</span><span class="sxs-lookup"><span data-stu-id="328ea-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="328ea-104">應用程式通常是以根據使用者輸入建構訊息的方式來回應使用者。</span><span class="sxs-lookup"><span data-stu-id="328ea-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="328ea-105">例如，網站就經常以包含使用者姓名的特殊問候語來回應新登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="328ea-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="328ea-106"><xref:System.String?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別中有數個方法，可讓您以動態方式建構要在使用者介面中顯示的自訂字串。</span><span class="sxs-lookup"><span data-stu-id="328ea-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="328ea-107">這些方法也可協助您執行一些基本字串作業，例如從位元組陣列建立新的字串、比較字串值，以及修改現有的字串。</span><span class="sxs-lookup"><span data-stu-id="328ea-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="328ea-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="328ea-108">In This Section</span></span>  
 [<span data-ttu-id="328ea-109">建立新字串</span><span class="sxs-lookup"><span data-stu-id="328ea-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="328ea-110">描述將物件轉換為字串和組合字串的基本方式。</span><span class="sxs-lookup"><span data-stu-id="328ea-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="328ea-111">修剪和移除字元</span><span class="sxs-lookup"><span data-stu-id="328ea-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="328ea-112">描述如何修剪或移除字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="328ea-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="328ea-113">填補字串</span><span class="sxs-lookup"><span data-stu-id="328ea-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="328ea-114">描述如何將字元或空格插入字串中。</span><span class="sxs-lookup"><span data-stu-id="328ea-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="328ea-115">比較字串</span><span class="sxs-lookup"><span data-stu-id="328ea-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="328ea-116">描述如何比較兩個或多個字串的內容。</span><span class="sxs-lookup"><span data-stu-id="328ea-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="328ea-117">變更大小寫</span><span class="sxs-lookup"><span data-stu-id="328ea-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="328ea-118">描述如何變更字串內的字元大小寫。</span><span class="sxs-lookup"><span data-stu-id="328ea-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="328ea-119">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="328ea-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="328ea-120">描述如何使用 <xref:System.Text.StringBuilder> 類別來建立及修改動態字串物件。</span><span class="sxs-lookup"><span data-stu-id="328ea-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="328ea-121">操作說明：執行基本字串操作</span><span class="sxs-lookup"><span data-stu-id="328ea-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="328ea-122">示範如何使用基本字串作業。</span><span class="sxs-lookup"><span data-stu-id="328ea-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="328ea-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="328ea-123">Related Sections</span></span>  
 [<span data-ttu-id="328ea-124">.NET 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="328ea-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="328ea-125">描述如何將一個類型轉換為另一個類型。</span><span class="sxs-lookup"><span data-stu-id="328ea-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="328ea-126">格式化類型</span><span class="sxs-lookup"><span data-stu-id="328ea-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="328ea-127">描述如何使用格式規範來將字串格式化。</span><span class="sxs-lookup"><span data-stu-id="328ea-127">Describes how to format strings using format specifiers.</span></span>
