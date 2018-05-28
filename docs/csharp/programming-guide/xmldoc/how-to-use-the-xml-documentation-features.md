---
title: 如何：使用 XML 文件功能 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: d7f1f51040033cf25f7f1aefb04d249e6e028ca3
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="c8dcf-102">如何：使用 XML 文件功能 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c8dcf-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="c8dcf-103">下列範例提供已記載之類型的基本概觀。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8dcf-104">範例</span><span class="sxs-lookup"><span data-stu-id="c8dcf-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

<span data-ttu-id="c8dcf-105">這個範例會產生具有下列內容的 .xml 檔案：</span><span class="sxs-lookup"><span data-stu-id="c8dcf-105">The example generates an .xml file with the following contents:</span></span>

```xml  
<?xml version="1.0"?>  
<doc>  
 <assembly>  
 <name>xmlsample</name>  
 </assembly>  
 <members>  
 <member name="T:SomeClass">  
 <summary>  
 Class level summary documentation goes here.</summary>  
 <remarks>  
 Longer comments can be associated with a type or member  
 through the remarks tag</remarks>  
 </member>  
 <member name="F:SomeClass.m_Name">  
 <summary>  
 Store for the name property</summary>  
 </member>  
 <member name="M:SomeClass.#ctor">  
 <summary>The class constructor.</summary>  
 </member>  
 <member name="M:SomeClass.SomeMethod(System.String)">  
 <summary>  
 Description for SomeMethod.</summary>  
 <param name="s"> Parameter description for s goes here</param>  
 <seealso cref="T:System.String">  
 You can use the cref attribute on any tag to reference a type or member  
 and the compiler will check that the reference exists. </seealso>  
 </member>  
 <member name="M:SomeClass.SomeOtherMethod">  
 <summary>  
 Some other method. </summary>  
 <returns>  
 Return results are described through the returns tag.</returns>  
 <seealso cref="M:SomeClass.SomeMethod(System.String)">  
 Notice the use of the cref attribute to reference a specific method </seealso>  
 </member>  
 <member name="M:SomeClass.Main(System.String[])">  
 <summary>  
 The entry point for the application.  
 </summary>  
 <param name="args"> A list of command line arguments</param>  
 </member>  
 <member name="P:SomeClass.Name">  
 <summary>  
 Name property </summary>  
 <value>A value tag is used to describe the property value</value>  
 </member>  
 </members>  
</doc>   
```

## <a name="compiling-the-code"></a><span data-ttu-id="c8dcf-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c8dcf-106">Compiling the Code</span></span>  
 <span data-ttu-id="c8dcf-107">若要編譯範例，請輸入下列命令列：</span><span class="sxs-lookup"><span data-stu-id="c8dcf-107">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="c8dcf-108">這會建立 XML 檔案 XMLsample.xml，您可以在瀏覽器中或使用 TYPE 命令進行檢視。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-108">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c8dcf-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="c8dcf-109">Robust Programming</span></span>  
 <span data-ttu-id="c8dcf-110">XML 文件是以 /// 開頭。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-110">XML documentation starts with ///.</span></span> <span data-ttu-id="c8dcf-111">當您建立新的專案時，精靈會為您在開頭放入幾行 ///。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="c8dcf-112">這些註解在處理時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="c8dcf-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="c8dcf-113">文件必須是語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="c8dcf-114">如果 XML 的語式不正確，則會產生警告，而且文件檔案會包含註解，指出發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="c8dcf-115">開發人員可以自由建立自己的標記集合。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="c8dcf-116">有一組建議使用的標記 (請參閱[建議使用的文件註解標記](recommended-tags-for-documentation-comments.md))。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="c8dcf-117">其中一些建議的標記具有特殊意義：</span><span class="sxs-lookup"><span data-stu-id="c8dcf-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="c8dcf-118">\<param> 標記是用來描述參數。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="c8dcf-119">如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="c8dcf-120">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-120">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="c8dcf-121">`cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="c8dcf-122">編譯器會驗證此程式碼項目存在。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-122">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="c8dcf-123">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="c8dcf-124">編譯器在尋找 `cref` 屬性中所述的類型時，會遵守任何 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="c8dcf-125">Visual Studio 中的 IntelliSense 使用 \<summary> 標記來顯示類型或成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c8dcf-126">XML 檔案不會提供類型和成員的完整資訊 (例如，它不會包含任何類型資訊)。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="c8dcf-127">若要取得類型或成員的完整資訊，文件檔案在使用時必須能夠反映實際類型或成員。</span><span class="sxs-lookup"><span data-stu-id="c8dcf-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8dcf-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8dcf-128">See Also</span></span>  
 [<span data-ttu-id="c8dcf-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c8dcf-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c8dcf-130">/doc (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="c8dcf-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="c8dcf-131">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="c8dcf-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
