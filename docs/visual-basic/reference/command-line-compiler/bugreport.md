---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 02d84bceb0242988c70889ddd5d3dc7530f6e808
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793539"
---
# <a name="-bugreport"></a><span data-ttu-id="6b15b-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="6b15b-102">-bugreport</span></span>

<span data-ttu-id="6b15b-103">建立檔案，您可以在提出 bug 報告時使用。</span><span class="sxs-lookup"><span data-stu-id="6b15b-103">Creates a file that you can use when you file a bug report.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b15b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b15b-104">Syntax</span></span>

```console
-bugreport:file
```

## <a name="arguments"></a><span data-ttu-id="6b15b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6b15b-105">Arguments</span></span>

|<span data-ttu-id="6b15b-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="6b15b-106">Term</span></span>|<span data-ttu-id="6b15b-107">定義</span><span class="sxs-lookup"><span data-stu-id="6b15b-107">Definition</span></span>|
|---|---|
|`file`|<span data-ttu-id="6b15b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="6b15b-108">Required.</span></span> <span data-ttu-id="6b15b-109">將包含 bug 報告的檔案名。</span><span class="sxs-lookup"><span data-stu-id="6b15b-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="6b15b-110">如果名稱包含空格，請用引號（""）括住檔案名。</span><span class="sxs-lookup"><span data-stu-id="6b15b-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b15b-111">備註</span><span class="sxs-lookup"><span data-stu-id="6b15b-111">Remarks</span></span>

<span data-ttu-id="6b15b-112">下列資訊會新增至 `file`：</span><span class="sxs-lookup"><span data-stu-id="6b15b-112">The following information is added to `file`:</span></span>

- <span data-ttu-id="6b15b-113">編譯中所有原始程式碼檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="6b15b-113">A copy of all source-code files in the compilation.</span></span>

- <span data-ttu-id="6b15b-114">編譯中使用的編譯器選項清單。</span><span class="sxs-lookup"><span data-stu-id="6b15b-114">A list of the compiler options used in the compilation.</span></span>

- <span data-ttu-id="6b15b-115">您的編譯器、通用語言執行時間和作業系統的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="6b15b-115">Version information about your compiler, common language runtime, and operating system.</span></span>

- <span data-ttu-id="6b15b-116">編譯器輸出 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6b15b-116">Compiler output, if any.</span></span>

- <span data-ttu-id="6b15b-117">問題的描述，會提示您。</span><span class="sxs-lookup"><span data-stu-id="6b15b-117">A description of the problem, for which you are prompted.</span></span>

- <span data-ttu-id="6b15b-118">您認為問題的說明應如何修正，而系統會提示您。</span><span class="sxs-lookup"><span data-stu-id="6b15b-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>

<span data-ttu-id="6b15b-119">因為所有原始程式碼檔的複本都包含在 `file`中，所以您可能會想要在最短的可能程式中重現（疑似）程式碼缺失。</span><span class="sxs-lookup"><span data-stu-id="6b15b-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b15b-120">`-bugreport` 選項會產生一個檔案，其中包含可能的機密資訊。</span><span class="sxs-lookup"><span data-stu-id="6b15b-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="6b15b-121">這包括目前時間、編譯器版本、.NET Framework 版本、作業系統版本、使用者名稱、編譯器執行時所使用的命令列引數、所有原始程式碼，以及任何參考元件的二進位格式。</span><span class="sxs-lookup"><span data-stu-id="6b15b-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="6b15b-122">藉由在 web.config 檔案中指定命令列選項來進行 ASP.NET 應用程式的伺服器端編譯，即可存取此選項。</span><span class="sxs-lookup"><span data-stu-id="6b15b-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="6b15b-123">若要避免這種情況，請修改 Machine.config 檔案，讓使用者不允許在伺服器上編譯。</span><span class="sxs-lookup"><span data-stu-id="6b15b-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>

<span data-ttu-id="6b15b-124">如果此選項與 `-errorreport:prompt`、`-errorreport:queue`或 `-errorreport:send`搭配使用，而您的應用程式發生編譯器內部錯誤，則 `file` 中的資訊會傳送給 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="6b15b-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="6b15b-125">這項資訊可協助 Microsoft 工程師找出錯誤的原因，並可協助改善下一版的 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="6b15b-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="6b15b-126">根據預設，不會將任何資訊傳送至 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="6b15b-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="6b15b-127">不過，當您使用 `-errorreport:queue`（預設會啟用）來編譯應用程式時，應用程式會收集其錯誤報表。</span><span class="sxs-lookup"><span data-stu-id="6b15b-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="6b15b-128">然後，在電腦的系統管理員登入時，錯誤報表系統會顯示一個快顯視窗，可讓系統管理員將登入後發生的任何錯誤報表轉寄給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="6b15b-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>

> [!NOTE]
> <span data-ttu-id="6b15b-129">Visual Studio 開發環境中無法使用 [`-bugreport`] 選項;只有當您從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="6b15b-129">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="6b15b-130">範例</span><span class="sxs-lookup"><span data-stu-id="6b15b-130">Example</span></span>

<span data-ttu-id="6b15b-131">下列範例會編譯*T2 .vb* ，並將所有 bug 報告資訊放在檔案*問題 .txt*中。</span><span class="sxs-lookup"><span data-stu-id="6b15b-131">The following example compiles *T2.vb* and puts all bug-reporting information in the file *Problem.txt*.</span></span>

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="6b15b-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b15b-132">See also</span></span>

- [<span data-ttu-id="6b15b-133">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="6b15b-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6b15b-134">-debug （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6b15b-134">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="6b15b-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="6b15b-135">-errorreport</span></span>](errorreport.md)
- [<span data-ttu-id="6b15b-136">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="6b15b-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="6b15b-137">[securityPolicy 的 trustLevel 元素（ASP.NET 設定架構）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b15b-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
