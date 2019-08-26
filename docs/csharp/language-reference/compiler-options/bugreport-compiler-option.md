---
title: -bugreport (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603077"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="21376-102">-bugreport (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="21376-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="21376-103">指定偵錯資訊應該置於檔案以供稍後分析。</span><span class="sxs-lookup"><span data-stu-id="21376-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21376-104">語法</span><span class="sxs-lookup"><span data-stu-id="21376-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="21376-105">引數</span><span class="sxs-lookup"><span data-stu-id="21376-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="21376-106">您要包含錯誤報告的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="21376-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21376-107">備註</span><span class="sxs-lookup"><span data-stu-id="21376-107">Remarks</span></span>  
 <span data-ttu-id="21376-108">**-bugreport** 選項會指定下列資訊應該置於 `file`：</span><span class="sxs-lookup"><span data-stu-id="21376-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="21376-109">編譯中所有原始程式碼檔的複本。</span><span class="sxs-lookup"><span data-stu-id="21376-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="21376-110">編譯中使用的編譯器選項清單。</span><span class="sxs-lookup"><span data-stu-id="21376-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="21376-111">您的編譯器、執行階段和作業系統的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="21376-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="21376-112">除了隨附於 .NET Framework 和 SDK 的組件之外，還包括參考組件和模組 (儲存為十六進位數字)。</span><span class="sxs-lookup"><span data-stu-id="21376-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="21376-113">編譯器輸出 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="21376-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="21376-114">問題的描述，會提示您操作指示。</span><span class="sxs-lookup"><span data-stu-id="21376-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="21376-115">您認為問題該如何解決的描述，會提示您操作指示。</span><span class="sxs-lookup"><span data-stu-id="21376-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="21376-116">如果這個選項與 **-errorreport:prompt** 或 **-errorreport:send** 搭配使用，則會將檔案中的資訊傳送給 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="21376-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="21376-117">由於 `file`中放置所有原始程式碼檔的複本，您可能想要以最短的可能程式重現 (可疑的) 程式碼缺失。</span><span class="sxs-lookup"><span data-stu-id="21376-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="21376-118">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="21376-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="21376-119">請注意，所產生檔案的內容會公開原始程式碼，而這可能會不慎洩漏資訊。</span><span class="sxs-lookup"><span data-stu-id="21376-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21376-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21376-120">See also</span></span>

- [<span data-ttu-id="21376-121">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="21376-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="21376-122">-errorreport (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="21376-122">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="21376-123">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="21376-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
