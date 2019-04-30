---
ms.openlocfilehash: acd87c6ad5de3621cc90e5f3e1566592a4eb7e46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747067"
---

<span data-ttu-id="691ea-101">若要使用底線字元作為前置分隔符號，您必須將下列項目新增至 Visual Basic 專案 (\*.vbproj) 檔：</span><span class="sxs-lookup"><span data-stu-id="691ea-101">To use the underscore character as a leading separator, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="691ea-102">如需詳細資訊，請參閱[設定的 Visual Basic 語言版本](../docs/visual-basic/language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="691ea-102">For more information see [setting the Visual Basic language version](../docs/visual-basic/language-reference/configure-language-version.md).</span></span>
