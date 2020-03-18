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
ms.openlocfilehash: 3352e7fc446ace391540360a3b6b36d604ca5f13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173753"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="7871a-102">-codepage (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="7871a-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="7871a-103">如果所需的頁面不是系統目前預設的字碼頁，這個選項可指定編譯期間使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="7871a-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7871a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7871a-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="7871a-105">引數</span><span class="sxs-lookup"><span data-stu-id="7871a-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="7871a-106">編譯過程中所有原始程式碼檔使用的字碼頁的 ID。</span><span class="sxs-lookup"><span data-stu-id="7871a-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7871a-107">備註</span><span class="sxs-lookup"><span data-stu-id="7871a-107">Remarks</span></span>  
 <span data-ttu-id="7871a-108">編譯器會先嘗試將所有原始程式檔解譯為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7871a-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="7871a-109">如果您的原始程式檔不是以 UTF-8 編碼，也不使用 7 位元的 ASCII 字元，則請使用 **-codepage** 選項指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="7871a-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="7871a-110">**-codepage** 會套用到您所編譯的所有原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="7871a-110">**-codepage** applies to all source code files in your compilation.</span></span>  

 <span data-ttu-id="7871a-111">如需如何尋找系統所支援之字碼頁的詳細資訊，請參閱 [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo)。</span><span class="sxs-lookup"><span data-stu-id="7871a-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="7871a-112">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="7871a-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7871a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7871a-113">See also</span></span>

- [<span data-ttu-id="7871a-114">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7871a-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7871a-115">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="7871a-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
