---
title: '如何使用 XML 檔功能-c # 程式設計手冊'
description: 瞭解如何使用 XML 檔功能。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 9ad2cfe62c70174eec9020ad4c8ce11608aca36d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380666"
---
# <a name="how-to-use-the-xml-documentation-features"></a>如何使用 XML 文件功能

下列範例提供已記載之類型的基本概觀。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

此範例會產生包含下列內容的 *.xml*檔案。

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯範例，請輸入下列命令：

`csc XMLsample.cs /doc:XMLsample.xml`

此命令會建立 XML 檔案*XMLsample.xml*，您可以在瀏覽器中或使用命令來查看該檔案 `TYPE` 。

## <a name="robust-programming"></a>穩固程式設計

XML 檔的開頭為 `///` 。 當您建立新的專案時，系統 `///` 會為您將一些入門行放在中。 這些註解在處理時有一些限制：

- 文件必須是語式正確的 XML。 如果 XML 的語式不正確，則會產生警告，而且文件檔案會包含註解，指出發生錯誤。

- 開發人員可以自由建立自己的標記集合。 有一[組建議的標記](recommended-tags-for-documentation-comments.md)。 其中一些建議的標記具有特殊意義：

  - `<param>`標記是用來描述參數。 如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。 如果驗證失敗，編譯器會發出警告。

  - `cref`屬性可以附加至任何標記，以參考程式碼元素。 編譯器會驗證此程式碼項目存在。 如果驗證失敗，編譯器會發出警告。 編譯器在尋找 `cref` 屬性中所述的類型時，會遵守任何 `using` 陳述式。

  - `<summary>`Visual Studio 內的 IntelliSense 會使用此標記來顯示類型或成員的其他資訊。

    > [!NOTE]
    > XML 檔案不會提供類型和成員的完整資訊 (例如，它不會包含任何類型資訊)。 若要取得有關類型或成員的完整資訊，請搭配實際類型或成員的反映使用檔檔。

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [-doc （c # 編譯器選項）](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML 文件註解](./index.md)
- [DocFX 檔處理器](https://dotnet.github.io/docfx/)
- [Sandcastle 這類檔處理器](https://github.com/EWSoftware/SHFB)
