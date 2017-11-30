---
title: ".NET Framework 中的基本字串作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f241b99f97cad081a65fd8654169e444a1b588cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="3780f-102">在.NET 中的基本字串作業</span><span class="sxs-lookup"><span data-stu-id="3780f-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="3780f-103">應用程式通常是以根據使用者輸入建構訊息的方式來回應使用者。</span><span class="sxs-lookup"><span data-stu-id="3780f-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="3780f-104">例如，網站就經常以包含使用者姓名的特殊問候語來回應新登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="3780f-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="3780f-105">中的某些方法<xref:System.String?displayProperty=nameWithType>和<xref:System.Text.StringBuilder?displayProperty=nameWithType>類別可讓您以動態方式建構您的使用者介面中顯示自訂字串。</span><span class="sxs-lookup"><span data-stu-id="3780f-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="3780f-106">這些方法也可協助您執行一些基本字串作業，例如從位元組陣列建立新的字串、比較字串值，以及修改現有的字串。</span><span class="sxs-lookup"><span data-stu-id="3780f-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3780f-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="3780f-107">In This Section</span></span>  
 [<span data-ttu-id="3780f-108">建立新字串</span><span class="sxs-lookup"><span data-stu-id="3780f-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="3780f-109">說明基本的方式，來將物件轉換成字串，並將字串合併。</span><span class="sxs-lookup"><span data-stu-id="3780f-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="3780f-110">修剪和移除字元</span><span class="sxs-lookup"><span data-stu-id="3780f-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="3780f-111">描述如何修剪或移除字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="3780f-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="3780f-112">填補字串</span><span class="sxs-lookup"><span data-stu-id="3780f-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="3780f-113">描述如何將字元或空格插入字串中。</span><span class="sxs-lookup"><span data-stu-id="3780f-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="3780f-114">比較字串</span><span class="sxs-lookup"><span data-stu-id="3780f-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="3780f-115">說明如何比較兩個或多個字串的內容。</span><span class="sxs-lookup"><span data-stu-id="3780f-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="3780f-116">變更大小寫</span><span class="sxs-lookup"><span data-stu-id="3780f-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="3780f-117">描述如何變更字串中字元的大小寫。</span><span class="sxs-lookup"><span data-stu-id="3780f-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="3780f-118">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="3780f-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="3780f-119">描述如何建立和修改與動態字串物件<xref:System.Text.StringBuilder>類別。</span><span class="sxs-lookup"><span data-stu-id="3780f-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="3780f-120">操作說明：執行基本字串操作</span><span class="sxs-lookup"><span data-stu-id="3780f-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="3780f-121">示範如何使用基本字串作業。</span><span class="sxs-lookup"><span data-stu-id="3780f-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3780f-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="3780f-122">Related Sections</span></span>  
 [<span data-ttu-id="3780f-123">.NET 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="3780f-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="3780f-124">描述如何將一個類型轉換成另一種類型。</span><span class="sxs-lookup"><span data-stu-id="3780f-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="3780f-125">格式化類型</span><span class="sxs-lookup"><span data-stu-id="3780f-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="3780f-126">描述如何格式化字串時，使用格式規範。</span><span class="sxs-lookup"><span data-stu-id="3780f-126">Describes how to format strings using format specifiers.</span></span>
