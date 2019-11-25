---
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b906178abf8d159083d95e41448596d512e857de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348581"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="36509-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36509-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="36509-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span><span class="sxs-lookup"><span data-stu-id="36509-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="36509-104">`-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。</span><span class="sxs-lookup"><span data-stu-id="36509-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="36509-105">語法</span><span class="sxs-lookup"><span data-stu-id="36509-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="36509-106">備註</span><span class="sxs-lookup"><span data-stu-id="36509-106">Remarks</span></span>

<span data-ttu-id="36509-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span><span class="sxs-lookup"><span data-stu-id="36509-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="36509-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span><span class="sxs-lookup"><span data-stu-id="36509-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="36509-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span><span class="sxs-lookup"><span data-stu-id="36509-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="36509-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="36509-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="36509-111">`-refonly` 和 [`-refout`](refout-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="36509-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="36509-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="36509-112">See also</span></span>

- [<span data-ttu-id="36509-113">-refout</span><span class="sxs-lookup"><span data-stu-id="36509-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="36509-114">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="36509-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="36509-115">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="36509-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
