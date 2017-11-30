---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a><span data-ttu-id="f945e-102">/langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f945e-102">/langversion (Visual Basic)</span></span>
<span data-ttu-id="f945e-103">可讓編譯器接受包含在指定的 Visual Basic 語言版本的語法。</span><span class="sxs-lookup"><span data-stu-id="f945e-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f945e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f945e-104">Syntax</span></span>  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="f945e-105">引數</span><span class="sxs-lookup"><span data-stu-id="f945e-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="f945e-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="f945e-106">Required.</span></span> <span data-ttu-id="f945e-107">要在編譯期間使用的語言版本。</span><span class="sxs-lookup"><span data-stu-id="f945e-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="f945e-108">接受的值為`9`， `9.0`， `10`，和`10.0`。</span><span class="sxs-lookup"><span data-stu-id="f945e-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f945e-109">備註</span><span class="sxs-lookup"><span data-stu-id="f945e-109">Remarks</span></span>  
 <span data-ttu-id="f945e-110">`/langversion`選項指定何種編譯器接受的語法。</span><span class="sxs-lookup"><span data-stu-id="f945e-110">The `/langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="f945e-111">例如，如果您指定的語言版本是 9.0，編譯器會產生只適用於 10.0 版及更新版本的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="f945e-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="f945e-112">當您開發該目標的不同版本的.NET framework 應用程式時，您可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="f945e-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="f945e-113">例如，如果您的目標.NET Framework 3.5，您可以使用此選項以確保不會使用從 10.0 版的語言語法。</span><span class="sxs-lookup"><span data-stu-id="f945e-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="f945e-114">您可以設定`/langversion`直接只能藉由使用命令列。</span><span class="sxs-lookup"><span data-stu-id="f945e-114">You can set `/langversion` directly only by using the command line.</span></span> <span data-ttu-id="f945e-115">如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)。</span><span class="sxs-lookup"><span data-stu-id="f945e-115">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f945e-116">範例</span><span class="sxs-lookup"><span data-stu-id="f945e-116">Example</span></span>  
 <span data-ttu-id="f945e-117">下列程式碼編譯`sample.vb`的 Visual Basic 9.0。</span><span class="sxs-lookup"><span data-stu-id="f945e-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f945e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f945e-118">See Also</span></span>  
 [<span data-ttu-id="f945e-119">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f945e-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f945e-120">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="f945e-120">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="f945e-121">以特定的 .NET Framework 版本為目標</span><span class="sxs-lookup"><span data-stu-id="f945e-121">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
