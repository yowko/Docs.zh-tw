---
title: "如何：使用 XML 文件功能 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb647a275a5cd5fac2316706591440d9792861b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="126e6-102">如何：使用 XML 文件功能 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="126e6-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="126e6-103">下列範例提供已記載之類型的基本概觀。</span><span class="sxs-lookup"><span data-stu-id="126e6-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="126e6-104">範例</span><span class="sxs-lookup"><span data-stu-id="126e6-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 <span data-ttu-id="126e6-105">**// 此 .xml 檔案是透過上述程式碼範例所產生。**</span><span class="sxs-lookup"><span data-stu-id="126e6-105">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="126e6-106">**\<?xml version="1.0"?>**</span><span class="sxs-lookup"><span data-stu-id="126e6-106">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="126e6-107">**\<doc>**</span><span class="sxs-lookup"><span data-stu-id="126e6-107">**\<doc>**</span></span>  
 <span data-ttu-id="126e6-108">**\<assembly>**</span><span class="sxs-lookup"><span data-stu-id="126e6-108">**\<assembly>**</span></span>  
 <span data-ttu-id="126e6-109">**\<name>xmlsample\</name>**</span><span class="sxs-lookup"><span data-stu-id="126e6-109">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="126e6-110">**\</assembly>**</span><span class="sxs-lookup"><span data-stu-id="126e6-110">**\</assembly>**</span></span>  
 <span data-ttu-id="126e6-111">**\<members>**</span><span class="sxs-lookup"><span data-stu-id="126e6-111">**\<members>**</span></span>  
 <span data-ttu-id="126e6-112">**\<member name="T:SomeClass">**</span><span class="sxs-lookup"><span data-stu-id="126e6-112">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="126e6-113">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-113">**\<summary>**</span></span>  
 <span data-ttu-id="126e6-114">**類別層級摘要文件在此處出現。\</summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-114">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="126e6-115">**\<remarks>**</span><span class="sxs-lookup"><span data-stu-id="126e6-115">**\<remarks>**</span></span>  
 <span data-ttu-id="126e6-116">**較長的註解可以是類型或成員相關聯**</span><span class="sxs-lookup"><span data-stu-id="126e6-116">**Longer comments can be associated with a type or member**</span></span>  
 <span data-ttu-id="126e6-117">**和類型或成員產生關聯\</remarks>**</span><span class="sxs-lookup"><span data-stu-id="126e6-117">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="126e6-118">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="126e6-118">**\</member>**</span></span>  
 <span data-ttu-id="126e6-119">**\<member name="F:SomeClass.m_Name">**</span><span class="sxs-lookup"><span data-stu-id="126e6-119">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="126e6-120">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-120">**\<summary>**</span></span>  
 <span data-ttu-id="126e6-121">**Name 屬性的存放區\</summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-121">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="126e6-122">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="126e6-122">**\</member>**</span></span>  
 <span data-ttu-id="126e6-123">**\<member name="M:SomeClass.#ctor">**</span><span class="sxs-lookup"><span data-stu-id="126e6-123">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="126e6-124">**\<摘要 > 的類別建構函式。\<摘要/>**</span><span class="sxs-lookup"><span data-stu-id="126e6-124">**\<summary>The class constructor.\</summary>**</span></span>  
 <span data-ttu-id="126e6-125">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="126e6-125">**\</member>**</span></span>  
 <span data-ttu-id="126e6-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="126e6-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="126e6-127">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-127">**\<summary>**</span></span>  
 <span data-ttu-id="126e6-128">**SomeMethod 的描述。\</summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-128">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="126e6-129">**\<param name="s"> s 的參數描述在此處出現\</param>**</span><span class="sxs-lookup"><span data-stu-id="126e6-129">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="126e6-130">**\<seealso cref="T:System.String">**</span><span class="sxs-lookup"><span data-stu-id="126e6-130">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="126e6-131">**您也可以任何標記上使用的 cref 屬性，參考類型或成員**</span><span class="sxs-lookup"><span data-stu-id="126e6-131">**You can use the cref attribute on any tag to reference a type or member**</span></span>  
 <span data-ttu-id="126e6-132">**而編譯器會檢查這個參考是否存在。\</seealso>**</span><span class="sxs-lookup"><span data-stu-id="126e6-132">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="126e6-133">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="126e6-133">**\</member>**</span></span>  
 <span data-ttu-id="126e6-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span><span class="sxs-lookup"><span data-stu-id="126e6-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="126e6-135">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-135">**\<summary>**</span></span>  
 <span data-ttu-id="126e6-136">**一些其他方法。\</summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-136">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="126e6-137">**\<returns>**</span><span class="sxs-lookup"><span data-stu-id="126e6-137">**\<returns>**</span></span>  
 <span data-ttu-id="126e6-138">**傳回結果是透過傳回標記描述。\</returns>**</span><span class="sxs-lookup"><span data-stu-id="126e6-138">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="126e6-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="126e6-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="126e6-140">**請注意使用 cref 屬性來參考特定的方法 \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="126e6-140">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="126e6-141">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="126e6-141">**\</member>**</span></span>  
 <span data-ttu-id="126e6-142">**\<member name="M:SomeClass.Main(System.String[])">**</span><span class="sxs-lookup"><span data-stu-id="126e6-142">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="126e6-143">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-143">**\<summary>**</span></span>  
 <span data-ttu-id="126e6-144">**應用程式的進入點。**</span><span class="sxs-lookup"><span data-stu-id="126e6-144">**The entry point for the application.**</span></span>  
 <span data-ttu-id="126e6-145">**\</summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-145">**\</summary>**</span></span>  
 <span data-ttu-id="126e6-146">**\<param name="args"> 命令列引數清單\</param>**</span><span class="sxs-lookup"><span data-stu-id="126e6-146">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="126e6-147">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="126e6-147">**\</member>**</span></span>  
 <span data-ttu-id="126e6-148">**\<member name="P:SomeClass.Name">**</span><span class="sxs-lookup"><span data-stu-id="126e6-148">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="126e6-149">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-149">**\<summary>**</span></span>  
 <span data-ttu-id="126e6-150">**Name 屬性 \</summary>**</span><span class="sxs-lookup"><span data-stu-id="126e6-150">**Name property \</summary>**</span></span>  
 <span data-ttu-id="126e6-151">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="126e6-151">**\<value>**</span></span>  
 <span data-ttu-id="126e6-152">**值的標記被用來描述這個屬性值\</value>**</span><span class="sxs-lookup"><span data-stu-id="126e6-152">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="126e6-153">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="126e6-153">**\</member>**</span></span>  
 <span data-ttu-id="126e6-154">**\</members>**</span><span class="sxs-lookup"><span data-stu-id="126e6-154">**\</members>**</span></span>  
<span data-ttu-id="126e6-155">**\</doc>**</span><span class="sxs-lookup"><span data-stu-id="126e6-155">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="126e6-156">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="126e6-156">Compiling the Code</span></span>  
 <span data-ttu-id="126e6-157">若要編譯範例，請輸入下列命令列：</span><span class="sxs-lookup"><span data-stu-id="126e6-157">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="126e6-158">這會建立 XML 檔案 XMLsample.xml，您可以在瀏覽器中或使用 TYPE 命令進行檢視。</span><span class="sxs-lookup"><span data-stu-id="126e6-158">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="126e6-159">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="126e6-159">Robust Programming</span></span>  
 <span data-ttu-id="126e6-160">XML 文件是以 /// 開頭。</span><span class="sxs-lookup"><span data-stu-id="126e6-160">XML documentation starts with ///.</span></span> <span data-ttu-id="126e6-161">當您建立新的專案時，精靈會為您在開頭放入幾行 ///。</span><span class="sxs-lookup"><span data-stu-id="126e6-161">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="126e6-162">這些註解在處理時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="126e6-162">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="126e6-163">文件必須是語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="126e6-163">The documentation must be well-formed XML.</span></span> <span data-ttu-id="126e6-164">如果 XML 的語式不正確，則會產生警告，而且文件檔案會包含註解，指出發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="126e6-164">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="126e6-165">開發人員可以自由建立自己的標記集合。</span><span class="sxs-lookup"><span data-stu-id="126e6-165">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="126e6-166">有建議的標記集合 (請參閱＜進一步閱讀＞一節)。</span><span class="sxs-lookup"><span data-stu-id="126e6-166">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="126e6-167">其中一些建議的標記具有特殊意義：</span><span class="sxs-lookup"><span data-stu-id="126e6-167">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="126e6-168">\<param> 標記是用來描述參數。</span><span class="sxs-lookup"><span data-stu-id="126e6-168">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="126e6-169">如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。</span><span class="sxs-lookup"><span data-stu-id="126e6-169">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="126e6-170">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="126e6-170">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="126e6-171">`cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。</span><span class="sxs-lookup"><span data-stu-id="126e6-171">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="126e6-172">編譯器會驗證此程式碼項目存在。</span><span class="sxs-lookup"><span data-stu-id="126e6-172">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="126e6-173">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="126e6-173">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="126e6-174">編譯器在尋找 `cref` 屬性中所述的類型時，會遵守任何 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="126e6-174">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="126e6-175">Visual Studio 中的 IntelliSense 使用 \<summary> 標記來顯示類型或成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="126e6-175">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="126e6-176">XML 檔案不會提供類型和成員的完整資訊 (例如，它不會包含任何類型資訊)。</span><span class="sxs-lookup"><span data-stu-id="126e6-176">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="126e6-177">若要取得類型或成員的完整資訊，文件檔案在使用時必須能夠反映實際類型或成員。</span><span class="sxs-lookup"><span data-stu-id="126e6-177">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126e6-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="126e6-178">See Also</span></span>  
 [<span data-ttu-id="126e6-179">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="126e6-179">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="126e6-180">/doc （C# 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="126e6-180">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="126e6-181">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="126e6-181">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
