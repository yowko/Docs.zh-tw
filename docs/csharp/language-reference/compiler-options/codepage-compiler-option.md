---
title: -codepage (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 7cbd3ec1b2d134106c6c9429341f5603444dac27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693976"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="9e4d1-102">-codepage (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="9e4d1-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="9e4d1-103">如果所需的頁面不是系統目前預設的字碼頁，這個選項可指定編譯期間使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="9e4d1-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e4d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e4d1-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e4d1-105">引數</span><span class="sxs-lookup"><span data-stu-id="9e4d1-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="9e4d1-106">編譯過程中所有原始程式碼檔使用的字碼頁的 ID。</span><span class="sxs-lookup"><span data-stu-id="9e4d1-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e4d1-107">備註</span><span class="sxs-lookup"><span data-stu-id="9e4d1-107">Remarks</span></span>  
 <span data-ttu-id="9e4d1-108">如果您編譯一或多個不是使用電腦的預設字碼頁建立的原始程式碼檔，則可以使用 **-codepage** 選項指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="9e4d1-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="9e4d1-109">**-codepage** 會套用到您所編譯的所有原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="9e4d1-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="9e4d1-110">如果原始程式碼檔是使用您電腦中正在作用中的同一個字碼頁所建立的，或者原始程式碼檔是使用 UNICODE 或 UTF-8 所建立，則不需要使用 **-codepage**。</span><span class="sxs-lookup"><span data-stu-id="9e4d1-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="9e4d1-111">如需如何尋找系統所支援之字碼頁的詳細資訊，請參閱 [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo)。</span><span class="sxs-lookup"><span data-stu-id="9e4d1-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="9e4d1-112">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="9e4d1-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4d1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e4d1-113">See also</span></span>

- [<span data-ttu-id="9e4d1-114">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="9e4d1-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="9e4d1-115">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="9e4d1-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
