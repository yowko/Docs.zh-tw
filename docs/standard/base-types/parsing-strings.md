---
title: "在.NET 中剖析字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 811db42e04e73d7acbc03e303297b19fdf643384
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="fbe0f-102">在.NET 中剖析字串</span><span class="sxs-lookup"><span data-stu-id="fbe0f-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="fbe0f-103">剖析作業會將代表 .NET 基底類型的字串轉換成該基底類型。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="fbe0f-104">例如，剖析作業用來將字串轉換為浮點數或日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="fbe0f-105">最常用來執行剖析作業的方法是 `Parse` 方法。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="fbe0f-106">因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="fbe0f-107">只在格式化時使用該物件會實作<xref:System.IFormatProvider>介面，以提供區分文化特性格式資訊，剖析也會使用該物件會實作<xref:System.IFormatProvider>介面，以決定如何解譯的字串表示法.</span><span class="sxs-lookup"><span data-stu-id="fbe0f-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="fbe0f-108">如需詳細資訊，請參閱[格式化型別](../../../docs/standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbe0f-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="fbe0f-109">In This Section</span></span>  
 [<span data-ttu-id="fbe0f-110">剖析數值字串</span><span class="sxs-lookup"><span data-stu-id="fbe0f-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="fbe0f-111">描述如何將字串轉換成.NET 數字型別。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="fbe0f-112">剖析日期和時間字串</span><span class="sxs-lookup"><span data-stu-id="fbe0f-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="fbe0f-113">描述如何將字串轉換成.NET **DateTime**型別。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="fbe0f-114">剖析其他字串</span><span class="sxs-lookup"><span data-stu-id="fbe0f-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="fbe0f-115">描述如何將轉換成字串**Char**，**布林**，和**列舉**型別。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fbe0f-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="fbe0f-116">Related Sections</span></span>  
 [<span data-ttu-id="fbe0f-117">格式化類型</span><span class="sxs-lookup"><span data-stu-id="fbe0f-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="fbe0f-118">描述基本格式的概念，像是格式規範和格式提供者。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="fbe0f-119">.NET 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="fbe0f-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="fbe0f-120">描述如何將類型轉換。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="fbe0f-121">基底類型</span><span class="sxs-lookup"><span data-stu-id="fbe0f-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="fbe0f-122">描述您可以在.NET 基底類型執行的一般作業。</span><span class="sxs-lookup"><span data-stu-id="fbe0f-122">Describes common operations that you can perform on .NET base types.</span></span>
