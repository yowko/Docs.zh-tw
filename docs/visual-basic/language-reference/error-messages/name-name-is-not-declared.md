---
title: 名稱 '<name>' 未宣告
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: dfa1d1600c7943e503b4f5ec2e2b8ecd6fbb9fe0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254193"
---
# <a name="name-name-is-not-declared"></a><span data-ttu-id="8e287-102">名稱 '\<name > ' 未宣告</span><span class="sxs-lookup"><span data-stu-id="8e287-102">Name '\<name>' is not declared</span></span>
<span data-ttu-id="8e287-103">語句參考了程式設計專案，但編譯器找不到具有該確切名稱的元素。</span><span class="sxs-lookup"><span data-stu-id="8e287-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="8e287-104">**錯誤識別碼：** BC30451</span><span class="sxs-lookup"><span data-stu-id="8e287-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e287-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8e287-105">To correct this error</span></span>  
  
1. <span data-ttu-id="8e287-106">請檢查參考陳述式中的名稱拼寫。</span><span class="sxs-lookup"><span data-stu-id="8e287-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="8e287-107">Visual Basic 不區分大小寫，但拼寫中的任何其他變化都會被視為完全不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e287-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="8e287-108">請注意，底線 (`_`) 是名稱的一部分，因此也是拼字的一部分。</span><span class="sxs-lookup"><span data-stu-id="8e287-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2. <span data-ttu-id="8e287-109">檢查物件及其成員之間是否有成員存取`.`運算子（）。</span><span class="sxs-lookup"><span data-stu-id="8e287-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="8e287-110">例如，如果您有 <xref:System.Windows.Forms.TextBox> 控制項，名為 `TextBox1`，那麼要存取它的 <xref:System.Windows.Forms.TextBoxBase.Text%2A> 屬性，您應該輸入 `TextBox1.Text`。</span><span class="sxs-lookup"><span data-stu-id="8e287-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="8e287-111">如果您改為輸入 `TextBox1Text`，便會建立不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e287-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3. <span data-ttu-id="8e287-112">如果拼寫正確，且任何物件成員存取的語法都正確，請確認已宣告該元素。</span><span class="sxs-lookup"><span data-stu-id="8e287-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="8e287-113">如需詳細資訊，請參閱宣告的[元素](../../programming-guide/language-features/declared-elements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8e287-113">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4. <span data-ttu-id="8e287-114">如果已宣告程式設計項目，請檢查它是否在範圍內。</span><span class="sxs-lookup"><span data-stu-id="8e287-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="8e287-115">如果參考的語句不在宣告程式設計專案的區域之外，您可能需要限定專案名稱。</span><span class="sxs-lookup"><span data-stu-id="8e287-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="8e287-116">如需詳細資訊，請參閱 [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md)。</span><span class="sxs-lookup"><span data-stu-id="8e287-116">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>  

5. <span data-ttu-id="8e287-117">如果您不是使用完整型別或型別和成員名稱（例如，您的程式碼將屬性參考為`MethodInfo.Name` ， `System.Reflection.MethodInfo.Name`而不是），請加入[Imports 語句](../statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="8e287-117">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="8e287-118">如果您嘗試編譯 SDK 樣式的專案（vbproj 檔案開頭為行\* `<Project Sdk="Microsoft.NET.Sdk">`的專案），且錯誤訊息參考到類型或成員，則會將您的應用程式設定為使用 Visual Basic 執行時間程式庫的參考進行編譯。</span><span class="sxs-lookup"><span data-stu-id="8e287-118">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="8e287-119">根據預設，程式庫的子集會內嵌在 SDK 樣式專案的元件中。</span><span class="sxs-lookup"><span data-stu-id="8e287-119">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="8e287-120">例如，下列範例無法編譯，因為<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName>找不到方法。</span><span class="sxs-lookup"><span data-stu-id="8e287-120">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="8e287-121">它不會內嵌在應用程式隨附的 Visual Basic 執行時間子集。</span><span class="sxs-lookup"><span data-stu-id="8e287-121">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   <span data-ttu-id="8e287-122">若要解決這個錯誤，請`<VBRuntime>Default</VBRuntime>`將專案新增至`<PropertyGroup>` [專案] 區段，如下列 Visual Basic 專案檔所示。</span><span class="sxs-lookup"><span data-stu-id="8e287-122">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="8e287-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e287-123">See also</span></span>

- [<span data-ttu-id="8e287-124">宣告和常數摘要</span><span class="sxs-lookup"><span data-stu-id="8e287-124">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="8e287-125">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="8e287-125">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="8e287-126">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="8e287-126">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="8e287-127">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="8e287-127">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
