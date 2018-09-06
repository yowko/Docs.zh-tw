---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8aee51df3ba9f92ca662fbbfbd73998e4a3b4538
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882600"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="6c5f9-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c5f9-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="6c5f9-103">指定編譯過程中所有原始程式碼檔使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c5f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c5f9-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="6c5f9-105">引數</span><span class="sxs-lookup"><span data-stu-id="6c5f9-105">Arguments</span></span>  
  
|<span data-ttu-id="6c5f9-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="6c5f9-106">Term</span></span>|<span data-ttu-id="6c5f9-107">定義</span><span class="sxs-lookup"><span data-stu-id="6c5f9-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="6c5f9-108">必要。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-108">Required.</span></span> <span data-ttu-id="6c5f9-109">編譯器會使用指定的字碼頁`id`來解譯原始程式檔的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c5f9-110">備註</span><span class="sxs-lookup"><span data-stu-id="6c5f9-110">Remarks</span></span>  
 <span data-ttu-id="6c5f9-111">若要編譯原始程式碼，以特定的編碼方式儲存，您可以使用`-codepage`指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="6c5f9-112">`-codepage`選項會套用至您所編譯的所有原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="6c5f9-113">如需詳細資訊，請參閱 < [.NET Framework 中的字元編碼](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-113">For more information, see [Character Encoding in the .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="6c5f9-114">`-codepage`如果原始程式檔已儲存的簽章中使用目前的 ANSI 字碼頁、 Unicode 或 utf-8，則不需要 選項。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="6c5f9-115">Visual Studio 會儲存所有的原始程式檔與目前的 ANSI 字碼頁預設情況下，除非使用者指定中的另一個編碼**編碼** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="6c5f9-116">Visual Studio 會使用**編碼**對話方塊以開啟原始程式碼檔使用不同的字碼頁儲存。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c5f9-117">`-codepage`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="6c5f9-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5f9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c5f9-118">See Also</span></span>  
 [<span data-ttu-id="6c5f9-119">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="6c5f9-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
