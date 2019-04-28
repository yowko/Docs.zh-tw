---
title: 其他資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 4808d87322d5b21b70ec38e2eb31b2b204938745
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008237"
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="771e0-102">其他資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="771e0-102">Miscellaneous Data Types (Visual Basic)</span></span>
<span data-ttu-id="771e0-103">Visual Basic 提供幾種資料類型不是目標數字或字元。</span><span class="sxs-lookup"><span data-stu-id="771e0-103">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="771e0-104">相反地，它們會處理特殊資料這類是/否值，日期/時間值和物件位址。</span><span class="sxs-lookup"><span data-stu-id="771e0-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="771e0-105">資料表中顯示的 Visual Basic 資料類型的並排顯示比較，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="771e0-105">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="771e0-106">布林值類型</span><span class="sxs-lookup"><span data-stu-id="771e0-106">Boolean Type</span></span>  
 <span data-ttu-id="771e0-107">[布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是不帶正負號的值，會解譯為其中一個`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="771e0-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="771e0-108">它的資料寬度取決於實作的平台。</span><span class="sxs-lookup"><span data-stu-id="771e0-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="771e0-109">如果是/否或是開/關，變數可以包含只有兩個狀態例如 true/false 的值，將它宣告為`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="771e0-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="771e0-110">日期類型</span><span class="sxs-lookup"><span data-stu-id="771e0-110">Date Type</span></span>  
 <span data-ttu-id="771e0-111">[日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)是 64 位元值，會保留日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="771e0-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="771e0-112">每個增量會代表西曆日曆 1 年的 1 年 1 月開始 （上午 12:00） 之後的經過時間的 100 奈秒。</span><span class="sxs-lookup"><span data-stu-id="771e0-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="771e0-113">如果變數可以包含日期值、 時間值，或兩者，將它宣告為`Date`。</span><span class="sxs-lookup"><span data-stu-id="771e0-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="771e0-114">物件類型</span><span class="sxs-lookup"><span data-stu-id="771e0-114">Object Type</span></span>  
 <span data-ttu-id="771e0-115">[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)是指向您的應用程式或其他一些應用程式中的物件執行個體的 32 位元位址。</span><span class="sxs-lookup"><span data-stu-id="771e0-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="771e0-116">`Object`變數可以參考任何物件辨識出您的應用程式，或任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="771e0-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="771e0-117">這同時包含*實值型別*，這類`Integer`， `Boolean`，和結構的執行個體，並*參考型別*，這是執行個體，例如建立類別的物件`String`和<xref:System.Windows.Forms.Form>，和陣列執行個體。</span><span class="sxs-lookup"><span data-stu-id="771e0-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="771e0-118">如果變數會儲存在編譯時期不知道類別的執行個體的指標，或者它可以指向各種資料類型的資料，將它宣告為`Object`。</span><span class="sxs-lookup"><span data-stu-id="771e0-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="771e0-119">利用`Object`資料型別時，您可以使用它來儲存任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="771e0-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="771e0-120">缺點是會產生額外的作業需要更多的執行時間，讓您的應用程式執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="771e0-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="771e0-121">如果您使用`Object`實值型別變數，您需要支付*boxing*並*unboxing*。</span><span class="sxs-lookup"><span data-stu-id="771e0-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="771e0-122">如果您使用參考型別，會產生*晚期繫結*。</span><span class="sxs-lookup"><span data-stu-id="771e0-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771e0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="771e0-123">See also</span></span>

- [<span data-ttu-id="771e0-124">類型字元</span><span class="sxs-lookup"><span data-stu-id="771e0-124">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="771e0-125">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="771e0-125">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="771e0-126">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="771e0-126">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="771e0-127">字元資料類型</span><span class="sxs-lookup"><span data-stu-id="771e0-127">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [<span data-ttu-id="771e0-128">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="771e0-128">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="771e0-129">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="771e0-129">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
