---
title: -字碼頁（Visual Basic）
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: e4cdc27ab021fe055f157b78946538f2b76870e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002368"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="f5eb7-102">-字碼頁（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f5eb7-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="f5eb7-103">指定編譯過程中所有原始程式碼檔使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5eb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5eb7-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5eb7-105">引數</span><span class="sxs-lookup"><span data-stu-id="f5eb7-105">Arguments</span></span>  
  
|<span data-ttu-id="f5eb7-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f5eb7-106">Term</span></span>|<span data-ttu-id="f5eb7-107">定義</span><span class="sxs-lookup"><span data-stu-id="f5eb7-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="f5eb7-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-108">Required.</span></span> <span data-ttu-id="f5eb7-109">編譯器會使用 `id` 指定的字碼頁來解讀來源檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5eb7-110">備註</span><span class="sxs-lookup"><span data-stu-id="f5eb7-110">Remarks</span></span>  
 <span data-ttu-id="f5eb7-111">若要編譯以特定編碼方式儲存的原始程式碼，您可以使用 `-codepage` 來指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="f5eb7-112">@No__t-0 選項會套用至編譯中的所有原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="f5eb7-113">如需詳細資訊，請參閱[.NET Framework 中的字元編碼](../../../standard/base-types/character-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="f5eb7-114">如果原始程式碼檔案是使用目前的 ANSI 字碼頁、Unicode 或 UTF-8 （含簽章）儲存，則不需要 `-codepage` 選項。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="f5eb7-115">Visual Studio 預設會儲存目前 ANSI 字碼頁的所有原始程式碼檔，除非使用者在 [**編碼**] 對話方塊中指定另一種編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="f5eb7-116">Visual Studio 使用 [**編碼**] 對話方塊來開啟以不同字碼頁儲存的原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5eb7-117">@No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="f5eb7-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5eb7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5eb7-118">See also</span></span>

- [<span data-ttu-id="f5eb7-119">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f5eb7-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
