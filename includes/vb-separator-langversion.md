---
ms.openlocfilehash: acd87c6ad5de3621cc90e5f3e1566592a4eb7e46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "61747067"
---

<span data-ttu-id="69bba-101">若要使用底線字元作為前置分隔符號，您必須將下列項目新增至 Visual Basic 專案 (\*.vbproj) 檔：</span><span class="sxs-lookup"><span data-stu-id="69bba-101">To use the underscore character as a leading separator, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="69bba-102">有關詳細資訊[，請參閱設置視覺化基礎語言版本](../docs/visual-basic/language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="69bba-102">For more information see [setting the Visual Basic language version](../docs/visual-basic/language-reference/configure-language-version.md).</span></span>
