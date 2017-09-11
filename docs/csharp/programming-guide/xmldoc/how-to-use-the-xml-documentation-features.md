---
title: "如何：使用 XML 文件功能 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eeee77db523bc0ad97f425d4ba8076ae5740dfe8
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="b77e5-102">如何：使用 XML 文件功能 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b77e5-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="b77e5-103">下列範例提供已記載之類型的基本概觀。</span><span class="sxs-lookup"><span data-stu-id="b77e5-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b77e5-104">範例</span><span class="sxs-lookup"><span data-stu-id="b77e5-104">Example</span></span>  
 <span data-ttu-id="b77e5-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b77e5-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span></span>  
  
 <span data-ttu-id="b77e5-106">**// 此 .xml 檔案是透過上述程式碼範例所產生。**</span><span class="sxs-lookup"><span data-stu-id="b77e5-106">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="b77e5-107">**\<?xml version="1.0"?>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-107">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="b77e5-108">**\<doc>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-108">**\<doc>**</span></span>  
 <span data-ttu-id="b77e5-109">**\<assembly>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-109">**\<assembly>**</span></span>  
 <span data-ttu-id="b77e5-110">**\<name>xmlsample\</name>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-110">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="b77e5-111">**\</assembly>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-111">**\</assembly>**</span></span>  
 <span data-ttu-id="b77e5-112">**\<members>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-112">**\<members>**</span></span>  
 <span data-ttu-id="b77e5-113">**\<member name="T:SomeClass">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-113">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="b77e5-114">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-114">**\<summary>**</span></span>  
 <span data-ttu-id="b77e5-115">**類別層級摘要文件在此處出現。\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-115">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="b77e5-116">**\<remarks>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-116">**\<remarks>**</span></span>  
 <span data-ttu-id="b77e5-117">**可以將較長的註解經由備註標記** </span><span class="sxs-lookup"><span data-stu-id="b77e5-117">**Longer comments can be associated with a type or member** </span></span>  
 <span data-ttu-id="b77e5-118">**和類型或成員產生關聯\</remarks>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-118">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="b77e5-119">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-119">**\</member>**</span></span>  
 <span data-ttu-id="b77e5-120">**\<member name="F:SomeClass.m_Name">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-120">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="b77e5-121">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-121">**\<summary>**</span></span>  
 <span data-ttu-id="b77e5-122">**Name 屬性的存放區\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-122">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="b77e5-123">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-123">**\</member>**</span></span>  
 <span data-ttu-id="b77e5-124">**\<member name="M:SomeClass.#ctor">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-124">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="b77e5-125">**\<summary>類別建構函式。\</summary>** </span><span class="sxs-lookup"><span data-stu-id="b77e5-125">**\<summary>The class constructor.\</summary>** </span></span>  
 <span data-ttu-id="b77e5-126">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-126">**\</member>**</span></span>  
 <span data-ttu-id="b77e5-127">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-127">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="b77e5-128">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-128">**\<summary>**</span></span>  
 <span data-ttu-id="b77e5-129">**SomeMethod 的描述。\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-129">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="b77e5-130">**\<param name="s"> s 的參數描述在此處出現\</param>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-130">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="b77e5-131">**\<seealso cref="T:System.String">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-131">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="b77e5-132">**您可以使用任何標記上的 cref 屬性來參考類型或成員** </span><span class="sxs-lookup"><span data-stu-id="b77e5-132">**You can use the cref attribute on any tag to reference a type or member** </span></span>  
 <span data-ttu-id="b77e5-133">**而編譯器會檢查這個參考是否存在。\</seealso>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-133">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="b77e5-134">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-134">**\</member>**</span></span>  
 <span data-ttu-id="b77e5-135">**\<member name="M:SomeClass.SomeOtherMethod">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-135">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="b77e5-136">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-136">**\<summary>**</span></span>  
 <span data-ttu-id="b77e5-137">**一些其他方法。\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-137">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="b77e5-138">**\<returns>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-138">**\<returns>**</span></span>  
 <span data-ttu-id="b77e5-139">**傳回結果是透過傳回標記描述。\</returns>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-139">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="b77e5-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="b77e5-141">**請注意使用 cref 屬性來參考特定的方法 \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-141">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="b77e5-142">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-142">**\</member>**</span></span>  
 <span data-ttu-id="b77e5-143">**\<member name="M:SomeClass.Main(System.String[])">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-143">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="b77e5-144">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-144">**\<summary>**</span></span>  
 <span data-ttu-id="b77e5-145">**應用程式的進入點。**</span><span class="sxs-lookup"><span data-stu-id="b77e5-145">**The entry point for the application.**</span></span>  
 <span data-ttu-id="b77e5-146">**\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-146">**\</summary>**</span></span>  
 <span data-ttu-id="b77e5-147">**\<param name="args"> 命令列引數清單\</param>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-147">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="b77e5-148">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-148">**\</member>**</span></span>  
 <span data-ttu-id="b77e5-149">**\<member name="P:SomeClass.Name">**</span><span class="sxs-lookup"><span data-stu-id="b77e5-149">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="b77e5-150">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-150">**\<summary>**</span></span>  
 <span data-ttu-id="b77e5-151">**Name 屬性 \</summary>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-151">**Name property \</summary>**</span></span>  
 <span data-ttu-id="b77e5-152">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-152">**\<value>**</span></span>  
 <span data-ttu-id="b77e5-153">**值的標記被用來描述這個屬性值\</value>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-153">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="b77e5-154">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-154">**\</member>**</span></span>  
 <span data-ttu-id="b77e5-155">**\</members>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-155">**\</members>**</span></span>  
<span data-ttu-id="b77e5-156">**\</doc>**</span><span class="sxs-lookup"><span data-stu-id="b77e5-156">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="b77e5-157">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b77e5-157">Compiling the Code</span></span>  
 <span data-ttu-id="b77e5-158">若要編譯範例，請輸入下列命令列：</span><span class="sxs-lookup"><span data-stu-id="b77e5-158">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="b77e5-159">這會建立 XML 檔案 XMLsample.xml，您可以在瀏覽器中或使用 TYPE 命令進行檢視。</span><span class="sxs-lookup"><span data-stu-id="b77e5-159">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b77e5-160">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="b77e5-160">Robust Programming</span></span>  
 <span data-ttu-id="b77e5-161">XML 文件是以 /// 開頭。</span><span class="sxs-lookup"><span data-stu-id="b77e5-161">XML documentation starts with ///.</span></span> <span data-ttu-id="b77e5-162">當您建立新的專案時，精靈會為您在開頭放入幾行 ///。</span><span class="sxs-lookup"><span data-stu-id="b77e5-162">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="b77e5-163">這些註解在處理時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="b77e5-163">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="b77e5-164">文件必須是語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="b77e5-164">The documentation must be well-formed XML.</span></span> <span data-ttu-id="b77e5-165">如果 XML 的語式不正確，則會產生警告，而且文件檔案會包含註解，指出發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b77e5-165">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="b77e5-166">開發人員可以自由建立自己的標記集合。</span><span class="sxs-lookup"><span data-stu-id="b77e5-166">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="b77e5-167">有建議的標記集合 (請參閱＜進一步閱讀＞一節)。</span><span class="sxs-lookup"><span data-stu-id="b77e5-167">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="b77e5-168">其中一些建議的標記具有特殊意義：</span><span class="sxs-lookup"><span data-stu-id="b77e5-168">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="b77e5-169">\<param> 標記是用來描述參數。</span><span class="sxs-lookup"><span data-stu-id="b77e5-169">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="b77e5-170">如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。</span><span class="sxs-lookup"><span data-stu-id="b77e5-170">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="b77e5-171">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="b77e5-171">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="b77e5-172">`cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。</span><span class="sxs-lookup"><span data-stu-id="b77e5-172">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="b77e5-173">編譯器會驗證此程式碼項目存在。</span><span class="sxs-lookup"><span data-stu-id="b77e5-173">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="b77e5-174">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="b77e5-174">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="b77e5-175">編譯器在尋找 `cref` 屬性中所述的類型時，會遵守任何 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b77e5-175">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="b77e5-176">Visual Studio 中的 IntelliSense 使用 \<summary> 標記來顯示類型或成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="b77e5-176">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b77e5-177">XML 檔案不會提供類型和成員的完整資訊 (例如，它不會包含任何類型資訊)。</span><span class="sxs-lookup"><span data-stu-id="b77e5-177">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="b77e5-178">若要取得類型或成員的完整資訊，文件檔案在使用時必須能夠反映實際類型或成員。</span><span class="sxs-lookup"><span data-stu-id="b77e5-178">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77e5-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b77e5-179">See Also</span></span>  
 <span data-ttu-id="b77e5-180">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b77e5-180">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b77e5-181">[/doc (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="b77e5-181">[/doc (C# Compiler Options)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span></span>  
 [<span data-ttu-id="b77e5-182">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="b77e5-182">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

