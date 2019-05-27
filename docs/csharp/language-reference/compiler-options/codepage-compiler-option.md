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
ms.openlocfilehash: 59dc1abc3f678a4cf15543c11f9f200ff318ce8f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876918"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="0d4dc-102">-codepage (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="0d4dc-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="0d4dc-103">如果所需的頁面不是系統目前預設的字碼頁，這個選項可指定編譯期間使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d4dc-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d4dc-105">引數</span><span class="sxs-lookup"><span data-stu-id="0d4dc-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="0d4dc-106">編譯過程中所有原始程式碼檔使用的字碼頁的 ID。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d4dc-107">備註</span><span class="sxs-lookup"><span data-stu-id="0d4dc-107">Remarks</span></span>  
 <span data-ttu-id="0d4dc-108">編譯器會先嘗試將所有原始程式檔解譯為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="0d4dc-109">如果您的原始程式檔不是以 UTF-8 編碼，也不使用 7 位元的 ASCII 字元，則請使用 **-codepage** 選項指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="0d4dc-110">**-codepage** 會套用到您所編譯的所有原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="0d4dc-111">如需如何尋找系統所支援之字碼頁的詳細資訊，請參閱 [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo)。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="0d4dc-112">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4dc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d4dc-113">See also</span></span>

- [<span data-ttu-id="0d4dc-114">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="0d4dc-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="0d4dc-115">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="0d4dc-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
