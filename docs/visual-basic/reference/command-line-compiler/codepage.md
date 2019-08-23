---
title: -字碼頁 (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 3a5974a910303f847679f18c23e00cfaa00caa2c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962607"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="dbd3e-102">-字碼頁 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbd3e-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="dbd3e-103">指定編譯過程中所有原始程式碼檔使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbd3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbd3e-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="dbd3e-105">引數</span><span class="sxs-lookup"><span data-stu-id="dbd3e-105">Arguments</span></span>  
  
|<span data-ttu-id="dbd3e-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="dbd3e-106">Term</span></span>|<span data-ttu-id="dbd3e-107">定義</span><span class="sxs-lookup"><span data-stu-id="dbd3e-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="dbd3e-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-108">Required.</span></span> <span data-ttu-id="dbd3e-109">編譯器會使用所指定`id`的字碼頁來解讀來源檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbd3e-110">備註</span><span class="sxs-lookup"><span data-stu-id="dbd3e-110">Remarks</span></span>  
 <span data-ttu-id="dbd3e-111">若要編譯以特定編碼方式儲存的原始程式碼, 您可以`-codepage`使用來指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="dbd3e-112">此`-codepage`選項適用于編譯中的所有原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="dbd3e-113">如需詳細資訊, 請參閱[.NET Framework 中的字元編碼](../../../standard/base-types/character-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="dbd3e-114">如果原始程式碼檔案是使用目前的 ANSI 字碼頁、Unicode 或 utf-8 (含簽章) 儲存, 則不需要選項。`-codepage`</span><span class="sxs-lookup"><span data-stu-id="dbd3e-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="dbd3e-115">Visual Studio 預設會儲存目前 ANSI 字碼頁的所有原始程式碼檔, 除非使用者在 [**編碼**] 對話方塊中指定另一種編碼方式。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="dbd3e-116">Visual Studio 使用 [**編碼**] 對話方塊來開啟以不同字碼頁儲存的原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbd3e-117">此`-codepage`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="dbd3e-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd3e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbd3e-118">See also</span></span>

- [<span data-ttu-id="dbd3e-119">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="dbd3e-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
