---
description: -bugreport (C# 編譯器選項)
title: -bugreport (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 1fb2efc9b12680e95767746c7e4e1ddacbdd2594
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "93281502"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="1cffa-103">-bugreport (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="1cffa-103">-bugreport (C# Compiler Options)</span></span>

<span data-ttu-id="1cffa-104">指定偵錯資訊應該置於檔案以供稍後分析。</span><span class="sxs-lookup"><span data-stu-id="1cffa-104">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cffa-105">語法</span><span class="sxs-lookup"><span data-stu-id="1cffa-105">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1cffa-106">引數</span><span class="sxs-lookup"><span data-stu-id="1cffa-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="1cffa-107">您要包含錯誤報告的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1cffa-107">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cffa-108">備註</span><span class="sxs-lookup"><span data-stu-id="1cffa-108">Remarks</span></span>  

 <span data-ttu-id="1cffa-109">**-bugreport** 選項會指定下列資訊應該置於 `file`：</span><span class="sxs-lookup"><span data-stu-id="1cffa-109">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="1cffa-110">編譯中所有原始程式碼檔的複本。</span><span class="sxs-lookup"><span data-stu-id="1cffa-110">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="1cffa-111">編譯中使用的編譯器選項清單。</span><span class="sxs-lookup"><span data-stu-id="1cffa-111">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="1cffa-112">您的編譯器、執行階段和作業系統的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="1cffa-112">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="1cffa-113">參考的元件和模組（儲存為十六進位數位），但隨附于 .NET 和 .NET SDK 的元件除外。</span><span class="sxs-lookup"><span data-stu-id="1cffa-113">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that are shipped with .NET and the .NET SDK.</span></span>  
  
- <span data-ttu-id="1cffa-114">編譯器輸出 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="1cffa-114">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="1cffa-115">問題的描述，會提示您操作指示。</span><span class="sxs-lookup"><span data-stu-id="1cffa-115">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="1cffa-116">您認為問題該如何解決的描述，會提示您操作指示。</span><span class="sxs-lookup"><span data-stu-id="1cffa-116">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="1cffa-117">如果這個選項與 **-errorreport:prompt** 或 **-errorreport:send** 搭配使用，則會將檔案中的資訊傳送給 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="1cffa-117">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="1cffa-118">由於 `file`中放置所有原始程式碼檔的複本，您可能想要以最短的可能程式重現 (可疑的) 程式碼缺失。</span><span class="sxs-lookup"><span data-stu-id="1cffa-118">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="1cffa-119">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="1cffa-119">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="1cffa-120">請注意，所產生檔案的內容會公開原始程式碼，而這可能會不慎洩漏資訊。</span><span class="sxs-lookup"><span data-stu-id="1cffa-120">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cffa-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cffa-121">See also</span></span>

- [<span data-ttu-id="1cffa-122">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1cffa-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1cffa-123">-errorreport (c # 編譯器選項) </span><span class="sxs-lookup"><span data-stu-id="1cffa-123">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="1cffa-124">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="1cffa-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
