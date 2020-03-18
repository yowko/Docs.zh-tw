---
title: 文檔注釋的推薦標記 - C# 程式設計指南
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789718"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>文檔注釋的推薦標籤（C# 程式設計指南）

C# 編譯器會處理程式碼中的文件註解，並將其在 **/doc** 命令列選項中指定其名稱的檔案中格式化為 XML。 要基於編譯器生成的檔創建最終文檔，您可以創建自訂工具，或使用[DocFX](https://dotnet.github.io/docfx/)或[Sandcastle](https://github.com/EWSoftware/SHFB)等工具。

標記是在類型和類型成員這類程式碼建構上處理。

> [!NOTE]
> 文件註解不能套用至命名空間。  
  
 編譯器會處理任何為有效 XML 的標記。 下列標記提供使用者文件中的常用功能。  
  
## <a name="tags"></a>Tags  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<第>段](./para.md)|[\<見>](./see.md)*|[\<值>](./value.md)  
|[\<代碼>](./code.md)|[\<參數>](./param.md)*|[\<也看到>](./seealso.md)*|  
|[\<示例>](./example.md)|[\<帕>](./paramref.md)|[\<摘要>](./summary.md)|  
|[\<異常>](./exception.md)*|[\<許可權>](./permission.md)*|[\<類型帕拉姆>](./typeparam.md)*|  
|[\<包括>](./include.md)*|[\<評論>](./remarks.md)|[\<類型帕阿姆夫>](./typeparamref.md)|  
|[\<清單>](./list.md)|[\<繼承>](./inheritdoc.md)|[\<返回>](./returns.md)|
  
（\*表示編譯器驗證語法。

如果您想要讓角括弧出現在文件註解的文字中，請使用 `<` 和 `>` 的 HTML 編碼，其分別為 `&lt;` 和 `&gt;`。 此編碼顯示在以下示例中。

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [-文檔（C# 編譯器選項）](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML 文件註解](./index.md)
