---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 4b468b8ee4301693312e9545396f2b9f495f75d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550907"
---
# <a name="-bugreport"></a><span data-ttu-id="094f4-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="094f4-102">-bugreport</span></span>

<span data-ttu-id="094f4-103">建立您在提出錯誤報表時可以使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="094f4-103">Creates a file that you can use when you file a bug report.</span></span>

## <a name="syntax"></a><span data-ttu-id="094f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="094f4-104">Syntax</span></span>

```console
-bugreport:file
```

## <a name="arguments"></a><span data-ttu-id="094f4-105">引數</span><span class="sxs-lookup"><span data-stu-id="094f4-105">Arguments</span></span>

|<span data-ttu-id="094f4-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="094f4-106">Term</span></span>|<span data-ttu-id="094f4-107">定義</span><span class="sxs-lookup"><span data-stu-id="094f4-107">Definition</span></span>|
|---|---|
|`file`|<span data-ttu-id="094f4-108">必要。</span><span class="sxs-lookup"><span data-stu-id="094f4-108">Required.</span></span> <span data-ttu-id="094f4-109">將包含 bug 報告的檔案名。</span><span class="sxs-lookup"><span data-stu-id="094f4-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="094f4-110">以引號括住檔案名 ( "" ) 如果名稱包含空格。</span><span class="sxs-lookup"><span data-stu-id="094f4-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|

## <a name="remarks"></a><span data-ttu-id="094f4-111">備註</span><span class="sxs-lookup"><span data-stu-id="094f4-111">Remarks</span></span>

<span data-ttu-id="094f4-112">下列資訊會加入至 `file` ：</span><span class="sxs-lookup"><span data-stu-id="094f4-112">The following information is added to `file`:</span></span>

- <span data-ttu-id="094f4-113">編譯中所有原始程式碼檔的複本。</span><span class="sxs-lookup"><span data-stu-id="094f4-113">A copy of all source-code files in the compilation.</span></span>

- <span data-ttu-id="094f4-114">編譯中所使用之編譯器選項的清單。</span><span class="sxs-lookup"><span data-stu-id="094f4-114">A list of the compiler options used in the compilation.</span></span>

- <span data-ttu-id="094f4-115">編譯器、common language runtime 和作業系統的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="094f4-115">Version information about your compiler, common language runtime, and operating system.</span></span>

- <span data-ttu-id="094f4-116">編譯器輸出 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="094f4-116">Compiler output, if any.</span></span>

- <span data-ttu-id="094f4-117">系統提示您的問題描述。</span><span class="sxs-lookup"><span data-stu-id="094f4-117">A description of the problem, for which you are prompted.</span></span>

- <span data-ttu-id="094f4-118">您應該如何解決問題的說明，將會提示您。</span><span class="sxs-lookup"><span data-stu-id="094f4-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>

<span data-ttu-id="094f4-119">由於中包含所有原始程式碼檔的複本 `file` ，因此您可能會想要在最短的程式中重現 (疑似) 程式碼缺失。</span><span class="sxs-lookup"><span data-stu-id="094f4-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="094f4-120">`-bugreport`選項會產生包含潛在敏感資訊的檔案。</span><span class="sxs-lookup"><span data-stu-id="094f4-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="094f4-121">這包括目前的時間、編譯器版本、.NET Framework 版本、作業系統版本、使用者名稱、編譯器執行時所使用的命令列引數、所有原始程式碼，以及任何參考元件的二進位格式。</span><span class="sxs-lookup"><span data-stu-id="094f4-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="094f4-122">您可以藉由在 ASP.NET 應用程式的伺服器端編譯 Web.config 檔案中指定命令列選項，來存取這個選項。</span><span class="sxs-lookup"><span data-stu-id="094f4-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="094f4-123">若要避免這種情況，請修改 Machine.config 檔案，以禁止使用者在伺服器上進行編譯。</span><span class="sxs-lookup"><span data-stu-id="094f4-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>

<span data-ttu-id="094f4-124">如果這個選項與 `-errorreport:prompt` 、或搭配使用 `-errorreport:queue` `-errorreport:send` ，而且您的應用程式發生編譯器內部錯誤，則中的資訊 `file` 會傳送至 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="094f4-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="094f4-125">這項資訊可協助 Microsoft 工程師找出錯誤的原因，並可協助改善下一版的 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="094f4-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="094f4-126">依預設，不會將任何資訊傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="094f4-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="094f4-127">但是，當您使用來編譯應用程式時， `-errorreport:queue` 預設會啟用此應用程式，而應用程式會收集其錯誤報表。</span><span class="sxs-lookup"><span data-stu-id="094f4-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="094f4-128">然後，當電腦的系統管理員登入時，錯誤報表系統就會顯示一個快顯視窗，讓系統管理員將登入之後發生的任何錯誤報表轉寄給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="094f4-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>

> [!NOTE]
> <span data-ttu-id="094f4-129">`-bugreport`選項無法在 Visual Studio 開發環境中使用; 只有當您從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="094f4-129">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="094f4-130">範例</span><span class="sxs-lookup"><span data-stu-id="094f4-130">Example</span></span>

<span data-ttu-id="094f4-131">下列範例會編譯 *T2* ，並將所有 bug 報告資訊放入 *Problem.txt*的檔案中。</span><span class="sxs-lookup"><span data-stu-id="094f4-131">The following example compiles *T2.vb* and puts all bug-reporting information in the file *Problem.txt*.</span></span>

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="094f4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="094f4-132">See also</span></span>

- [<span data-ttu-id="094f4-133">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="094f4-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="094f4-134">-debug (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="094f4-134">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="094f4-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="094f4-135">-errorreport</span></span>](errorreport.md)
- [<span data-ttu-id="094f4-136">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="094f4-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="094f4-137">[securityPolicy 的 trustLevel 項目 (ASP.NET 設定結構描述)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="094f4-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
