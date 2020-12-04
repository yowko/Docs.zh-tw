---
title: '檔規則 (程式碼分析) '
description: 瞭解程式碼分析規則檔規則
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96585322"
---
# <a name="documentation-rules"></a><span data-ttu-id="8cc3f-103">文件規則</span><span class="sxs-lookup"><span data-stu-id="8cc3f-103">Documentation rules</span></span>

<span data-ttu-id="8cc3f-104">檔規則支援透過正確使用外部可見 Api 的 [XML 檔批註](../../../csharp/codedoc.md) ，來撰寫妥善記載的程式庫。</span><span class="sxs-lookup"><span data-stu-id="8cc3f-104">Documentation rules support writing well-documented libraries through the correct use of [XML documentation comments](../../../csharp/codedoc.md) for externally visible APIs.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8cc3f-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="8cc3f-105">In this section</span></span>

| <span data-ttu-id="8cc3f-106">規則</span><span class="sxs-lookup"><span data-stu-id="8cc3f-106">Rule</span></span> | <span data-ttu-id="8cc3f-107">描述</span><span class="sxs-lookup"><span data-stu-id="8cc3f-107">Description</span></span> |
| - | - |
| [<span data-ttu-id="8cc3f-108">CA1200：請避免使用具有前置詞的 cref 標記</span><span class="sxs-lookup"><span data-stu-id="8cc3f-108">CA1200: Avoid using cref tags with a prefix</span></span>](ca1200.md) | <span data-ttu-id="8cc3f-109">XML 檔標記中的 [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) 屬性工作表示「程式碼參考」。</span><span class="sxs-lookup"><span data-stu-id="8cc3f-109">The [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) attribute in an XML documentation tag means "code reference".</span></span> <span data-ttu-id="8cc3f-110">它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="8cc3f-110">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="8cc3f-111">避免使用具有前置詞的 `cref` 標記，因為它會防止編譯器驗證參考。</span><span class="sxs-lookup"><span data-stu-id="8cc3f-111">Avoid using `cref` tags with prefixes, because it prevents the compiler from verifying references.</span></span> <span data-ttu-id="8cc3f-112">它也可防止 Visual Studio 整合式開發環境 (IDE) 在重構期間尋找和更新這些符號參考。</span><span class="sxs-lookup"><span data-stu-id="8cc3f-112">It also prevents the Visual Studio integrated development environment (IDE) from finding and updating these symbol references during refactorings.</span></span> |
