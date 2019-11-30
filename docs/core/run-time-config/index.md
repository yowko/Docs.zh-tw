---
title: 執行時間設定
description: 瞭解如何使用執行時間設定設定來設定 .NET Core 應用程式。
ms.date: 11/13/2019
ms.openlocfilehash: e3922f6df81198b5e122f16d5cfc4b6d15cbb4ae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567383"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="9600b-103">.NET Core 執行時間設定</span><span class="sxs-lookup"><span data-stu-id="9600b-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="9600b-104">.NET Core 支援使用設定檔和環境變數，在執行時間設定 .NET Core 應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="9600b-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="9600b-105">在下列情況中，執行時間設定是一個吸引人的選項：</span><span class="sxs-lookup"><span data-stu-id="9600b-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="9600b-106">您不會擁有或控制應用程式的原始程式碼，因此無法以程式設計方式進行設定。</span><span class="sxs-lookup"><span data-stu-id="9600b-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="9600b-107">應用程式的多個實例會在單一系統上同時執行，而您想要設定每個實例以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="9600b-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="9600b-108">本檔是進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="9600b-108">This documentation is a work in progress.</span></span> <span data-ttu-id="9600b-109">如果您發現此處顯示的資訊不完整或不正確，請[開啟問題](https://github.com/dotnet/docs/issues)讓我們知道，或[提交提取要求](https://github.com/dotnet/docs/pulls)以解決問題。</span><span class="sxs-lookup"><span data-stu-id="9600b-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="9600b-110">如需提交 dotnet/檔存放庫之提取要求的相關資訊，請參閱[參與者指南](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="9600b-110">For information on submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="9600b-111">.NET Core 提供下列機制，讓您在執行時間設定應用程式：</span><span class="sxs-lookup"><span data-stu-id="9600b-111">.NET Core provides the following mechanisms for configuring applications at run time:</span></span>

- <span data-ttu-id="9600b-112">[.Runtimeconfig.json json](#runtimeconfigjson)檔案</span><span class="sxs-lookup"><span data-stu-id="9600b-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="9600b-113">環境變數</span><span class="sxs-lookup"><span data-stu-id="9600b-113">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="9600b-114">檔集的這一節中的文章包含依類別目錄進行組織，例如，「偵測」和「垃圾收集」。</span><span class="sxs-lookup"><span data-stu-id="9600b-114">The articles in this section of the documentation include are organized by category, for example, debugging and garbage collection.</span></span> <span data-ttu-id="9600b-115">*.Runtimeconfig.json*會顯示可用的設定選項： [僅限 .net Core）]、[app.config （僅限 .NET Framework）]*和 [環境*變數]。</span><span class="sxs-lookup"><span data-stu-id="9600b-115">Available configuration options are shown for *runtimeconfig.json* (.NET Core only), *app.config* (.NET Framework only), and environment variables.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="9600b-116">.runtimeconfig.json json</span><span class="sxs-lookup"><span data-stu-id="9600b-116">runtimeconfig.json</span></span>

<span data-ttu-id="9600b-117">在 *.runtimeconfig.json*檔案的**configProperties**區段中，指定執行時間設定選項。</span><span class="sxs-lookup"><span data-stu-id="9600b-117">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* file.</span></span> <span data-ttu-id="9600b-118">本節的格式如下：</span><span class="sxs-lookup"><span data-stu-id="9600b-118">This section has the form:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

<span data-ttu-id="9600b-119">以下是範例檔案：</span><span class="sxs-lookup"><span data-stu-id="9600b-119">Here is an example file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

<span data-ttu-id="9600b-120">[Dotnet build](../tools/dotnet-build.md)命令會在組建目錄中自動建立 *.runtimeconfig.json*檔案。</span><span class="sxs-lookup"><span data-stu-id="9600b-120">The *runtimeconfig.json* file is automatically created in the build directory by the [dotnet build](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="9600b-121">當您在 Visual Studio 中選取 [**建立**] 功能表選項時，也會建立此檔案。</span><span class="sxs-lookup"><span data-stu-id="9600b-121">It's also created when you select the **Build** menu option in Visual Studio.</span></span> <span data-ttu-id="9600b-122">之後，您就可以在檔案建立後加以編輯。</span><span class="sxs-lookup"><span data-stu-id="9600b-122">You can then edit the file once it's created.</span></span>

<span data-ttu-id="9600b-123">某些設定值也可以藉由呼叫 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法，以程式設計方式進行設定。</span><span class="sxs-lookup"><span data-stu-id="9600b-123">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="9600b-124">環境變數</span><span class="sxs-lookup"><span data-stu-id="9600b-124">Environment variables</span></span>

<span data-ttu-id="9600b-125">環境變數可以用來提供一些執行時間設定資訊。</span><span class="sxs-lookup"><span data-stu-id="9600b-125">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="9600b-126">指定為環境變數的設定旋鈕通常會**COMPlus_** 前置詞。</span><span class="sxs-lookup"><span data-stu-id="9600b-126">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="9600b-127">您可以從 Windows [控制台]、命令列或以程式設計方式，在 Windows 和 Unix 系統上呼叫 <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> 方法，以定義環境變數。</span><span class="sxs-lookup"><span data-stu-id="9600b-127">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="9600b-128">下列範例示範如何在命令列設定環境變數：</span><span class="sxs-lookup"><span data-stu-id="9600b-128">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
