---
title: '建議使用的檔註解標記-c # 程式設計手冊'
description: 瞭解建議的檔註解標記。 查看建議的標記清單，並查看其他可用的資源。
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 65bca6f979c5ffd91507b571a4f049377315192d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381511"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>建議使用的檔註解標記（c # 程式設計手冊）

C# 編譯器會處理程式碼中的文件註解，並將其在 **/doc** 命令列選項中指定其名稱的檔案中格式化為 XML。 若要根據編譯器產生的檔案建立最終檔集，您可以建立自訂工具，或使用[DocFX](https://dotnet.github.io/docfx/)或[sandcastle 這類](https://github.com/EWSoftware/SHFB)等工具。

標記是在類型和類型成員這類程式碼建構上處理。

> [!NOTE]
> 文件註解不能套用至命名空間。  
  
 編譯器會處理任何為有效 XML 的標記。 下列標記提供使用者文件中的常用功能。  
  
## <a name="tags"></a>Tags  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
（ \* 表示編譯器會驗證語法。）

如果您想要讓角括弧出現在文件註解的文字中，請使用 `<` 和 `>` 的 HTML 編碼，其分別為 `&lt;` 和 `&gt;`。 此編碼方式如下列範例所示。

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [-doc （c # 編譯器選項）](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML 文件註解](./index.md)
