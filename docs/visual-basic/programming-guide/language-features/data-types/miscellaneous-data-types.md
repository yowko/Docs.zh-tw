---
title: 其他資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: cc6262b5bb305bb839917e222d831fa3340a1b14
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346340"
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="259e5-102">其他資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="259e5-102">Miscellaneous Data Types (Visual Basic)</span></span>
<span data-ttu-id="259e5-103">Visual Basic 提供幾個未導向數位或字元的資料類型。</span><span class="sxs-lookup"><span data-stu-id="259e5-103">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="259e5-104">相反地，它們會處理特定的資料，例如「是/否值」、「日期/時間值」和「物件位址」。</span><span class="sxs-lookup"><span data-stu-id="259e5-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="259e5-105">如需顯示 Visual Basic 資料類型並存比較的資料表，請參閱[資料類型](../../../../visual-basic/language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="259e5-105">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="259e5-106">布林值類型</span><span class="sxs-lookup"><span data-stu-id="259e5-106">Boolean Type</span></span>  
 <span data-ttu-id="259e5-107">[布林資料類型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是一種不帶正負號的值，會解讀為 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="259e5-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="259e5-108">其資料寬度取決於執行平臺。</span><span class="sxs-lookup"><span data-stu-id="259e5-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="259e5-109">如果變數只能包含兩個狀態值（例如 true/false、yes/no 或 on/off），請將它宣告為 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="259e5-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="259e5-110">日期類型</span><span class="sxs-lookup"><span data-stu-id="259e5-110">Date Type</span></span>  
 <span data-ttu-id="259e5-111">[Date 資料類型](../../../../visual-basic/language-reference/data-types/date-data-type.md)是同時保存日期和時間資訊的64位值。</span><span class="sxs-lookup"><span data-stu-id="259e5-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="259e5-112">每個增量代表西曆中第1年1月1日開始（12:00 AM）以來經過一段時間的100毫微秒。</span><span class="sxs-lookup"><span data-stu-id="259e5-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="259e5-113">如果變數可以包含日期值、時間值或兩者，請將它宣告為 `Date`。</span><span class="sxs-lookup"><span data-stu-id="259e5-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="259e5-114">物件類型</span><span class="sxs-lookup"><span data-stu-id="259e5-114">Object Type</span></span>  
 <span data-ttu-id="259e5-115">[Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)是32位位址，指向應用程式或其他應用程式中的物件實例。</span><span class="sxs-lookup"><span data-stu-id="259e5-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="259e5-116">`Object` 變數可以參考您的應用程式所辨識的任何物件，或是任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="259e5-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="259e5-117">這包括實*值*型別，例如 `Integer`、`Boolean`和結構實例，以及*參考*型別，這些都是從類別（例如 `String` 和 <xref:System.Windows.Forms.Form>和陣列實例）建立之物件的實例。</span><span class="sxs-lookup"><span data-stu-id="259e5-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="259e5-118">如果變數儲存的指標指向您在編譯時期不知道的類別實例，或如果它可以指向各種資料類型的資料，請將它宣告為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="259e5-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="259e5-119">`Object` 資料類型的優點是您可以使用它來儲存任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="259e5-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="259e5-120">缺點是您會產生額外的作業，以執行較長的執行時間，並讓您的應用程式執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="259e5-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="259e5-121">如果您使用 `Object` 變數做為實數值型別，則會產生*裝箱*和*取消裝箱*。</span><span class="sxs-lookup"><span data-stu-id="259e5-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="259e5-122">如果您將它用於參考型別，則會產生*晚期繫結*。</span><span class="sxs-lookup"><span data-stu-id="259e5-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="259e5-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="259e5-123">See also</span></span>

- [<span data-ttu-id="259e5-124">類型字元</span><span class="sxs-lookup"><span data-stu-id="259e5-124">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="259e5-125">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="259e5-125">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="259e5-126">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="259e5-126">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="259e5-127">字元資料類型</span><span class="sxs-lookup"><span data-stu-id="259e5-127">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [<span data-ttu-id="259e5-128">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="259e5-128">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="259e5-129">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="259e5-129">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
