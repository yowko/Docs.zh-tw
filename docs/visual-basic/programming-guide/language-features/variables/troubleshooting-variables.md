---
title: "在 Visual Basic 中的為變數進行疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ccf7ee3b0205dcd85d82c06e1822c4d3f9296a1c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-variables-in-visual-basic"></a><span data-ttu-id="0955b-102">在 Visual Basic 中為變數進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0955b-102">Troubleshooting Variables in Visual Basic</span></span>
<span data-ttu-id="0955b-103">此頁面會列出使用中的變數時所發生的一些常見問題[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0955b-103">This page lists some common problems that can occur when working with variables in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="unable-to-access-members-of-an-object"></a><span data-ttu-id="0955b-104">無法存取物件的成員</span><span class="sxs-lookup"><span data-stu-id="0955b-104">Unable to Access Members of an Object</span></span>  
 <span data-ttu-id="0955b-105">如果您的程式碼嘗試存取物件的屬性或方法，可能會發生兩種錯誤結果：</span><span class="sxs-lookup"><span data-stu-id="0955b-105">If your code attempts to access a property or method on an object, there are two possible error outcomes:</span></span>  
  
-   <span data-ttu-id="0955b-106">如果您宣告物件變數屬於特定類型，然後參考該類型未定義的成員，編譯器可能會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0955b-106">The compiler can generate an error message if you declare the object variable to be of a specific type and then refer to a member not defined by that type.</span></span>  
  
-   <span data-ttu-id="0955b-107">執行階段<xref:System.MemberAccessException>指派給物件變數的物件不會公開您的程式碼嘗試存取的成員時，會發生。</xref:System.MemberAccessException></span><span class="sxs-lookup"><span data-stu-id="0955b-107">A run-time <xref:System.MemberAccessException> occurs when the object assigned to an object variable does not expose the member your code is trying to access.</span></span> <span data-ttu-id="0955b-108">如果變數是[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)，您也可以取得此例外狀況，如果成員不是`Public`。</span><span class="sxs-lookup"><span data-stu-id="0955b-108">In the case of a variable of [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md), you can also get this exception if the member is not `Public`.</span></span> <span data-ttu-id="0955b-109">這是因為晚期繫結只允許存取 `Public` 成員。</span><span class="sxs-lookup"><span data-stu-id="0955b-109">This is because late binding allows access only to `Public` members.</span></span>  
  
 <span data-ttu-id="0955b-110">當[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)集合型別檢查`On`，只有方法和類別與您將其宣告的屬性，可存取物件變數。</span><span class="sxs-lookup"><span data-stu-id="0955b-110">When the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets type checking `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="0955b-111">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="0955b-111">The following example illustrates this.</span></span>  

 <span data-ttu-id="0955b-112">[!code-vb[VbVbalrVariables #&2;](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0955b-112">[!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]</span></span>  
  
 <span data-ttu-id="0955b-113">在此範例中，`p`可使用的成員<xref:System.Object>類別本身，也不會包含`Left`屬性。</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0955b-113">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="0955b-114">相反地，`q`已宣告型別<xref:System.Windows.Forms.Label>，因此它可以將所有方法和屬性<xref:System.Windows.Forms.Label>類別<xref:System.Windows.Forms>命名空間。</xref:System.Windows.Forms> </xref:System.Windows.Forms.Label> </xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="0955b-114">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
### <a name="correct-approach"></a><span data-ttu-id="0955b-115">正確方法</span><span class="sxs-lookup"><span data-stu-id="0955b-115">Correct Approach</span></span>  
 <span data-ttu-id="0955b-116">若要能夠存取特定類別之物件的所有成員，請盡可能宣告物件變數屬於該類別的類型。</span><span class="sxs-lookup"><span data-stu-id="0955b-116">To be able to access all the members of an object of a particular class, declare the object variable to be of the type of that class when possible.</span></span> <span data-ttu-id="0955b-117">如果您無法執行此作業，例如，如果您不知道在編譯時期所輸入的物件，您必須設定`Option Strict`至`Off`和宣告的變數[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="0955b-117">If you cannot do this, for example if you do not know the object type at compile time, you must set `Option Strict` to `Off` and declare the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="0955b-118">這樣就能將任何類型的物件指派給變數，您也應該採取步驟確認目前指派的物件屬於可接受的類型。</span><span class="sxs-lookup"><span data-stu-id="0955b-118">This allows objects of any type to be assigned to the variable, and you should take steps to ensure that the currently assigned object is of an acceptable type.</span></span> <span data-ttu-id="0955b-119">您可以使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來做出決定。</span><span class="sxs-lookup"><span data-stu-id="0955b-119">You can use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to make this determination.</span></span>  
  
## <a name="other-components-cannot-access-your-variable"></a><span data-ttu-id="0955b-120">其他元件無法存取您的變數</span><span class="sxs-lookup"><span data-stu-id="0955b-120">Other Components Cannot Access Your Variable</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0955b-121">名稱為*不區分大小寫*。</span><span class="sxs-lookup"><span data-stu-id="0955b-121"> names are *case-insensitive*.</span></span> <span data-ttu-id="0955b-122">如果兩個名稱只有字母大小寫不同，則編譯器會將它們解譯成相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="0955b-122">If two names differ in alphabetic case only, the compiler interprets them as the same name.</span></span> <span data-ttu-id="0955b-123">例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。</span><span class="sxs-lookup"><span data-stu-id="0955b-123">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="0955b-124">不過，Common Language Runtime (CLR) 使用 *區分大小寫* 的繫結。</span><span class="sxs-lookup"><span data-stu-id="0955b-124">However, the common language runtime (CLR) uses *case-sensitive* binding.</span></span> <span data-ttu-id="0955b-125">因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0955b-125">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="0955b-126">例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。</span><span class="sxs-lookup"><span data-stu-id="0955b-126">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="0955b-127">如果您隨後重新編譯類別，並將元素的名稱變更為 `abc`，則其他使用此類別的組件就無法再存取該元素。</span><span class="sxs-lookup"><span data-stu-id="0955b-127">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class can no longer access that element.</span></span> <span data-ttu-id="0955b-128">因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。</span><span class="sxs-lookup"><span data-stu-id="0955b-128">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
 <span data-ttu-id="0955b-129">如需詳細資訊，請參閱[Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)。</span><span class="sxs-lookup"><span data-stu-id="0955b-129">For more information, see [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span></span>  
  
### <a name="correct-approach"></a><span data-ttu-id="0955b-130">正確方法</span><span class="sxs-lookup"><span data-stu-id="0955b-130">Correct Approach</span></span>  
 <span data-ttu-id="0955b-131">若要讓其他元件能夠存取您的變數，請將其名稱視為區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0955b-131">To allow other components to access your variables, treat their names as if they were case-sensitive.</span></span> <span data-ttu-id="0955b-132">當您正在測試類別或模組時，請確定其他組件繫結至預定的變數。</span><span class="sxs-lookup"><span data-stu-id="0955b-132">When you are testing your class or module, make sure other assemblies are binding to the variables you expect them to.</span></span> <span data-ttu-id="0955b-133">一旦發行元件後，請勿修改現有的變數名稱，包括變更其大小寫。</span><span class="sxs-lookup"><span data-stu-id="0955b-133">Once you have published a component, do not make any modifications to existing variable names, including changing their cases.</span></span>  
  
## <a name="wrong-variable-being-used"></a><span data-ttu-id="0955b-134">使用錯誤的變數</span><span class="sxs-lookup"><span data-stu-id="0955b-134">Wrong Variable Being Used</span></span>  
 <span data-ttu-id="0955b-135">當您有多個變數具有相同的名稱，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器嘗試解析該名稱的每個參考。</span><span class="sxs-lookup"><span data-stu-id="0955b-135">When you have more than one variable with the same name, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler attempts to resolve each reference to that name.</span></span> <span data-ttu-id="0955b-136">如果變數具有不同的範圍，則編譯器會用最小的範圍來解析宣告的參考。</span><span class="sxs-lookup"><span data-stu-id="0955b-136">If the variables have different scope, the compiler resolves a reference to the declaration with the narrowest scope.</span></span> <span data-ttu-id="0955b-137">如果範圍相同，則解析會失敗，且編譯器會發出錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="0955b-137">If they have the same scope, the resolution fails and the compiler signals an error.</span></span> <span data-ttu-id="0955b-138">如需詳細資訊，請參閱[宣告之項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="0955b-138">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
### <a name="correct-approach"></a><span data-ttu-id="0955b-139">正確方法</span><span class="sxs-lookup"><span data-stu-id="0955b-139">Correct Approach</span></span>  
 <span data-ttu-id="0955b-140">避免使用具有相同名稱但不同範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="0955b-140">Avoid using variables with the same name but different scope.</span></span> <span data-ttu-id="0955b-141">如果您想要使用其他組件或專案，請盡可能避免使用這些外部元件所定義的任何名稱。</span><span class="sxs-lookup"><span data-stu-id="0955b-141">If you are using other assemblies or projects, avoid using any names defined in those external components as much as possible.</span></span> <span data-ttu-id="0955b-142">如果您有多個同名的變數時，請務必限定它的每個參考。</span><span class="sxs-lookup"><span data-stu-id="0955b-142">If you have more than one variable with the same name, be sure you qualify every reference to it.</span></span> <span data-ttu-id="0955b-143">如需詳細資訊，請參閱[宣告之項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="0955b-143">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0955b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0955b-144">See Also</span></span>  
 <span data-ttu-id="0955b-145">[變數](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-145">[Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="0955b-146"> [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-146"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="0955b-147"> [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-147"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="0955b-148"> [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-148"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="0955b-149"> [如何︰ 存取物件的成員](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-149"> [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span></span>  
<span data-ttu-id="0955b-150"> [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-150"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="0955b-151"> [如何︰ 決定物件變數參考的類型](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-151"> [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span></span>  
<span data-ttu-id="0955b-152"> [宣告項目參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="0955b-152"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="0955b-153"> [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)</span><span class="sxs-lookup"><span data-stu-id="0955b-153"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)</span></span>
