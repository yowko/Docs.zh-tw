---
title: "其他資料類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ed7b61a5ec57ff85347f2c257e321ab9ec425274
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="97d2f-102">其他資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97d2f-102">Miscellaneous Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="97d2f-103">提供數個不導向數字或字元資料型別。</span><span class="sxs-lookup"><span data-stu-id="97d2f-103"> supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="97d2f-104">相反地，它們會處理特定資料例如是/否值、 日期/時間值和物件位址。</span><span class="sxs-lookup"><span data-stu-id="97d2f-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="97d2f-105">顯示由並排比較資料表[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="97d2f-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="97d2f-106">布林型別</span><span class="sxs-lookup"><span data-stu-id="97d2f-106">Boolean Type</span></span>  
 <span data-ttu-id="97d2f-107">[布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是不帶正負號的值會解譯為`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="97d2f-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="97d2f-108">資料寬度取決於實作平台。</span><span class="sxs-lookup"><span data-stu-id="97d2f-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="97d2f-109">如果是/否或是開/關變數可以包含只有兩個狀態值 true/false 時，例如，將它宣告為`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="97d2f-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="97d2f-110">日期類型</span><span class="sxs-lookup"><span data-stu-id="97d2f-110">Date Type</span></span>  
 <span data-ttu-id="97d2f-111">[日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)是保存日期和時間資訊的 64 位元值。</span><span class="sxs-lookup"><span data-stu-id="97d2f-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="97d2f-112">每個增量 100 奈秒的時間 （上午 12:00） 開始之後的西曆的 1 年月 1。</span><span class="sxs-lookup"><span data-stu-id="97d2f-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="97d2f-113">如果變數可以包含日期值、 時間值，或兩者，將它宣告為`Date`。</span><span class="sxs-lookup"><span data-stu-id="97d2f-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="97d2f-114">物件類型</span><span class="sxs-lookup"><span data-stu-id="97d2f-114">Object Type</span></span>  
 <span data-ttu-id="97d2f-115">[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)是指向您的應用程式或其他應用程式中的物件執行個體的 32 位元位址。</span><span class="sxs-lookup"><span data-stu-id="97d2f-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="97d2f-116">`Object`變數可以參考您的應用程式可辨識的任何物件或任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="97d2f-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="97d2f-117">這同時包含*實值型別*，例如`Integer`， `Boolean`，和結構的執行個體，和*參考型別*，例如從類別建立物件的執行個體`String`和<xref:System.Windows.Forms.Form>，和陣列執行個體。</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="97d2f-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="97d2f-118">如果變數是儲存您不知道在編譯時期，類別的執行個體的指標，或可以指向各種資料類型的資料，將它宣告為`Object`。</span><span class="sxs-lookup"><span data-stu-id="97d2f-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="97d2f-119">利用`Object`資料型別是，可以用它來儲存任何資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="97d2f-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="97d2f-120">缺點是，您需支付額外的作業，可以執行更多的時間，使得應用程式執行變慢。</span><span class="sxs-lookup"><span data-stu-id="97d2f-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="97d2f-121">如果您使用`Object`實值型別變數，則會產生*boxing*和*unboxing*。</span><span class="sxs-lookup"><span data-stu-id="97d2f-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="97d2f-122">如果您使用參考類型，則會產生*晚期繫結*。</span><span class="sxs-lookup"><span data-stu-id="97d2f-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d2f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97d2f-123">See Also</span></span>  
 <span data-ttu-id="97d2f-124">[類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="97d2f-124">[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="97d2f-125"> [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="97d2f-125"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="97d2f-126"> [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="97d2f-126"> [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span></span>  
<span data-ttu-id="97d2f-127"> [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="97d2f-127"> [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span></span>  
<span data-ttu-id="97d2f-128"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="97d2f-128"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="97d2f-129"> [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="97d2f-129"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
