---
title: 其他資料類型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f80aacccab4c215b3e3917cc73097080aa6b9941
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="dd5e8-102">其他資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5e8-102">Miscellaneous Data Types (Visual Basic)</span></span>
<span data-ttu-id="dd5e8-103">Visual Basic 提供數個不導向數字或字元的資料類型。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-103">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="dd5e8-104">相反地，它們可以處理特定資料這類是/否值、 日期/時間值和物件位址。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="dd5e8-105">顯示的 Visual Basic 資料類型來並行比較表，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-105">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="dd5e8-106">布林型別</span><span class="sxs-lookup"><span data-stu-id="dd5e8-106">Boolean Type</span></span>  
 <span data-ttu-id="dd5e8-107">[布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是解譯為不帶正負號的值`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="dd5e8-108">它的資料寬度取決於實作的平台。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="dd5e8-109">如果是/否，或開啟/關閉變數可以包含只有兩個狀態例如 true/false 的值，將它宣告為`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="dd5e8-110">Date 類型</span><span class="sxs-lookup"><span data-stu-id="dd5e8-110">Date Type</span></span>  
 <span data-ttu-id="dd5e8-111">[日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)是保存日期和時間資訊的 64 位元值。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="dd5e8-112">每個增量代表 100 奈秒的經過時間 （上午 12:00） 起西曆日曆 1 年的 1 年 1 月。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="dd5e8-113">如果變數可以包含值，日期、 時間值，或兩者，將它宣告為`Date`。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="dd5e8-114">物件類型</span><span class="sxs-lookup"><span data-stu-id="dd5e8-114">Object Type</span></span>  
 <span data-ttu-id="dd5e8-115">[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)是指向您的應用程式或某些其他應用程式中的物件執行個體的 32 位元位址。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="dd5e8-116">`Object`變數可以參考任何物件，辨識您的應用程式，或任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="dd5e8-117">同時包含這*實值類型*，例如`Integer`， `Boolean`，和結構的執行個體，和*參考型別*，這是執行個體的物件透過類別建立的例如`String`和<xref:System.Windows.Forms.Form>，以及陣列執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="dd5e8-118">如果變數是儲存您不知道在編譯時期，類別的執行個體的指標，或可以指向不同的資料類型的資料，將它宣告為`Object`。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="dd5e8-119">優點`Object`資料類型是，您可以使用它來儲存任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="dd5e8-120">缺點是會產生額外的作業，需要更多的執行時間，使得您的應用程式執行變慢。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="dd5e8-121">如果您使用`Object`實值類型變數，您會產生*boxing*和*unboxing*。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="dd5e8-122">如果您使用參考類型，就發生*晚期繫結*。</span><span class="sxs-lookup"><span data-stu-id="dd5e8-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5e8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5e8-123">See Also</span></span>  
 [<span data-ttu-id="dd5e8-124">類型字元</span><span class="sxs-lookup"><span data-stu-id="dd5e8-124">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="dd5e8-125">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="dd5e8-125">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="dd5e8-126">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="dd5e8-126">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="dd5e8-127">字元資料類型</span><span class="sxs-lookup"><span data-stu-id="dd5e8-127">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [<span data-ttu-id="dd5e8-128">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="dd5e8-128">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="dd5e8-129">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="dd5e8-129">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
