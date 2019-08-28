---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows 上使用 .NET Core 執行適用於 Apache Spark 的 .NET 應用程式。
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577005"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="5ac07-103">教學課程：開始使用適用於 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="5ac07-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="5ac07-104">本教學課程將指導您如何在 Windows 上使用 .NET Core，執行適用於 Apache Spark 的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ac07-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="5ac07-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="5ac07-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="5ac07-106">為適用於 Apache Spark 的 .NET 準備您的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="5ac07-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="5ac07-107">下載 **Microsoft.Spark.Worker**</span><span class="sxs-lookup"><span data-stu-id="5ac07-107">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="5ac07-108">建置及執行適用於 Apache Spark 的 .NET 簡單應用程式</span><span class="sxs-lookup"><span data-stu-id="5ac07-108">Build and run a simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="5ac07-109">準備您的環境</span><span class="sxs-lookup"><span data-stu-id="5ac07-109">Prepare your environment</span></span>

<span data-ttu-id="5ac07-110">開始前，請確認您可以從命令列執行 `dotnet`、`java`、`mvn` 和 `spark-shell`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-110">Before you begin, make sure you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line.</span></span> <span data-ttu-id="5ac07-111">當您的環境準備就緒之後，請跳到下一節。</span><span class="sxs-lookup"><span data-stu-id="5ac07-111">If your environment is already prepared, you can skip to the next section.</span></span> <span data-ttu-id="5ac07-112">若您無法執行任何或所有的命令，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="5ac07-112">If you cannot run any or all of the commands, follow the steps below.</span></span>

1. <span data-ttu-id="5ac07-113">下載並安裝 [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-113">Download and install the [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="5ac07-114">安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。</span><span class="sxs-lookup"><span data-stu-id="5ac07-114">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> <span data-ttu-id="5ac07-115">使用 PowerShell 命令 `dotnet --version` 驗證安裝。</span><span class="sxs-lookup"><span data-stu-id="5ac07-115">Use the PowerShell command `dotnet --version` to verify the installation.</span></span>

2. <span data-ttu-id="5ac07-116">安裝包含最新更新的 [Visual Studio 2017](https://www.visualstudio.com/downloads/) 或 [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-116">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/) or [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) with the latest updates.</span></span> <span data-ttu-id="5ac07-117">您可以使用 Community、Professional 或 Enterprise。</span><span class="sxs-lookup"><span data-stu-id="5ac07-117">You can use Community, Professional, or Enterprise.</span></span> <span data-ttu-id="5ac07-118">Community 版本免費。</span><span class="sxs-lookup"><span data-stu-id="5ac07-118">The Community version is free.</span></span>

   <span data-ttu-id="5ac07-119">請在安裝期間選擇下列工作負載：</span><span class="sxs-lookup"><span data-stu-id="5ac07-119">Choose the following workloads during installation:</span></span>
      * <span data-ttu-id="5ac07-120">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="5ac07-120">.NET desktop development</span></span>
          * <span data-ttu-id="5ac07-121">所有必要元件</span><span class="sxs-lookup"><span data-stu-id="5ac07-121">All required components</span></span>
          * <span data-ttu-id="5ac07-122">.NET Framework 4.6.1 開發工具</span><span class="sxs-lookup"><span data-stu-id="5ac07-122">.NET Framework 4.6.1 Development Tools</span></span>
      * <span data-ttu-id="5ac07-123">.NET Core 跨平台開發</span><span class="sxs-lookup"><span data-stu-id="5ac07-123">.NET Core cross-platform development</span></span>
          * <span data-ttu-id="5ac07-124">所有必要元件</span><span class="sxs-lookup"><span data-stu-id="5ac07-124">All required components</span></span>

3. <span data-ttu-id="5ac07-125">安裝 [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-125">Install [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

    * <span data-ttu-id="5ac07-126">為您的作業系統選取適當版本。</span><span class="sxs-lookup"><span data-stu-id="5ac07-126">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="5ac07-127">例如，為 Windows x64 電腦選取 **jdk-8u201-windows-x64.exe**。</span><span class="sxs-lookup"><span data-stu-id="5ac07-127">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span>
    * <span data-ttu-id="5ac07-128">使用 PowerShell 命令 `java -version` 驗證安裝。</span><span class="sxs-lookup"><span data-stu-id="5ac07-128">Use the PowerShell command `java -version` to verify the installation.</span></span>

4. <span data-ttu-id="5ac07-129">安裝 [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-129">Install [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span></span>
    * <span data-ttu-id="5ac07-130">下載 [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-130">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
    * <span data-ttu-id="5ac07-131">解壓縮到本機目錄。</span><span class="sxs-lookup"><span data-stu-id="5ac07-131">Extract to a local directory.</span></span> <span data-ttu-id="5ac07-132">例如，`c:\bin\apache-maven-3.6.0\`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-132">For example, `c:\bin\apache-maven-3.6.0\`.</span></span>
    * <span data-ttu-id="5ac07-133">將 Apache Maven 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。</span><span class="sxs-lookup"><span data-stu-id="5ac07-133">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="5ac07-134">若解壓縮到 `c:\bin\apache-maven-3.6.0\`，就應將 `c:\bin\apache-maven-3.6.0\bin` 新增到您的 PATH 之中。</span><span class="sxs-lookup"><span data-stu-id="5ac07-134">If you extracted to `c:\bin\apache-maven-3.6.0\`, you would add `c:\bin\apache-maven-3.6.0\bin` to your PATH.</span></span>
    * <span data-ttu-id="5ac07-135">使用 PowerShell 命令 `mvn -version` 驗證安裝。</span><span class="sxs-lookup"><span data-stu-id="5ac07-135">Use the PowerShell command `mvn -version` to verify the installation.</span></span>

5. <span data-ttu-id="5ac07-136">安裝 [Apache Spark 2.3+](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-136">Install [Apache Spark 2.3+](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="5ac07-137">不支援 Apache Spark 2.4+。</span><span class="sxs-lookup"><span data-stu-id="5ac07-137">Apache Spark 2.4+ isn't supported.</span></span>
    * <span data-ttu-id="5ac07-138">下載 [Apache Spark 2.3+](https://spark.apache.org/downloads.html)，然後使用 [7-zip](https://www.7-zip.org/) 或 [WinZip](https://www.winzip.com/) 等工具，將其解壓縮到本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="5ac07-138">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder using a tool like [7-zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/).</span></span> <span data-ttu-id="5ac07-139">例如，您可以將其解壓縮到 `c:\bin\spark-2.3.2-bin-hadoop2.7\`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-139">For example, you might extract it to `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>
    * <span data-ttu-id="5ac07-140">將 Apache Spark 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。</span><span class="sxs-lookup"><span data-stu-id="5ac07-140">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="5ac07-141">若解壓縮到 `c:\bin\spark-2.3.2-bin-hadoop2.7\`，就應將 `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` 新增到您的 PATH 之中。</span><span class="sxs-lookup"><span data-stu-id="5ac07-141">If you extracted to `c:\bin\spark-2.3.2-bin-hadoop2.7\`, you would add `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` to your PATH.</span></span>
    * <span data-ttu-id="5ac07-142">新增名為 `SPARK_HOME` 的[新環境變數](https://www.java.com/en/download/help/path.xml)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-142">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) called `SPARK_HOME`.</span></span> <span data-ttu-id="5ac07-143">若解壓縮到 `C:\bin\spark-2.3.2-bin-hadoop2.7\`，請為**變數值**使用 `C:\bin\spark-2.3.2-bin-hadoop2.7\`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-143">If you extracted to `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use  `C:\bin\spark-2.3.2-bin-hadoop2.7\` for the **Variable value**.</span></span>
    * <span data-ttu-id="5ac07-144">驗證您能夠從命令列執行 `spark-shell`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-144">Verify you are able to run `spark-shell` from your command line.</span></span>

6. <span data-ttu-id="5ac07-145">設定 [WinUtils](https://github.com/steveloughran/winutils)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-145">Set up [WinUtils](https://github.com/steveloughran/winutils).</span></span>
    * <span data-ttu-id="5ac07-146">從 [WinUtils 存放庫](https://github.com/steveloughran/winutils)下載 **winutils.exe** 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="5ac07-146">Download the **winutils.exe** binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="5ac07-147">選取用以編譯 Spark 的 Hadoop 版本。</span><span class="sxs-lookup"><span data-stu-id="5ac07-147">Select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="5ac07-148">例如，您可以為 **Spark 2.3.2**使用 **hadoop-2.7.1**。</span><span class="sxs-lookup"><span data-stu-id="5ac07-148">For example, you use **hadoop-2.7.1** for **Spark 2.3.2**.</span></span> <span data-ttu-id="5ac07-149">Hadoop 版本會標註在您 Spark 安裝資料夾名稱的結尾。</span><span class="sxs-lookup"><span data-stu-id="5ac07-149">The Hadoop version is annotated at the end of your Spark install folder name.</span></span>
    * <span data-ttu-id="5ac07-150">將 **winutils.exe** 二進位檔儲存到您選擇的目錄。</span><span class="sxs-lookup"><span data-stu-id="5ac07-150">Save the **winutils.exe** binary to a directory of your choice.</span></span> <span data-ttu-id="5ac07-151">例如，`c:\hadoop\bin`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-151">For example, `c:\hadoop\bin`.</span></span>
    * <span data-ttu-id="5ac07-152">設定 `HADOOP_HOME` 以反映 **winutils.exe** 的目錄 (不含 `bin`)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-152">Set `HADOOP_HOME` to reflect the directory with **winutils.exe** without `bin`.</span></span> <span data-ttu-id="5ac07-153">例如，`c:\hadoop`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-153">For example, `c:\hadoop`.</span></span>
    * <span data-ttu-id="5ac07-154">設定 PATH 環境變數，將 `%HADOOP_HOME%\bin` 加入其中。</span><span class="sxs-lookup"><span data-stu-id="5ac07-154">Set the PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span>

<span data-ttu-id="5ac07-155">再次確認您可以從命令列執行 `dotnet`、`java`、`mvn` 和 `spark-shell`，然後前往下一節。</span><span class="sxs-lookup"><span data-stu-id="5ac07-155">Double check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="download-the-microsoftsparkworker-release"></a><span data-ttu-id="5ac07-156">下載 Microsoft.Spark.Worker 版本</span><span class="sxs-lookup"><span data-stu-id="5ac07-156">Download the Microsoft.Spark.Worker release</span></span>

1. <span data-ttu-id="5ac07-157">從適用於 Apache Spark 的 .NET GitHub 版本頁面，將發行的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) 下載到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="5ac07-157">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub Releases page to your local machine.</span></span> <span data-ttu-id="5ac07-158">例如，您可以將其下載到 `c:\bin\Microsoft.Spark.Worker\` 路徑。</span><span class="sxs-lookup"><span data-stu-id="5ac07-158">For example, you might download it to the path, `c:\bin\Microsoft.Spark.Worker\`.</span></span>

2. <span data-ttu-id="5ac07-159">建立名為 `DotnetWorkerPath` 的[新環境變數](https://www.java.com/en/download/help/path.xml)，並將其設為 **Microsoft.Spark.Worker** 的下載目錄，然後加以解壓縮。</span><span class="sxs-lookup"><span data-stu-id="5ac07-159">Create a [new environment variable](https://www.java.com/en/download/help/path.xml) called `DotnetWorkerPath` and set it to the directory where you downloaded and extracted the **Microsoft.Spark.Worker**.</span></span> <span data-ttu-id="5ac07-160">例如，`c:\bin\Microsoft.Spark.Worker`。</span><span class="sxs-lookup"><span data-stu-id="5ac07-160">For example, `c:\bin\Microsoft.Spark.Worker`.</span></span>

## <a name="clone-the-net-for-apache-spark-github-repo"></a><span data-ttu-id="5ac07-161">複製適用於 Apache Spark 的 .NET GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="5ac07-161">Clone the .NET for Apache Spark GitHub repo</span></span>

<span data-ttu-id="5ac07-162">使用下列 [GitBash](https://gitforwindows.org/) 命令，將適用於 Apache Spark 的 .NET 存放庫複製到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="5ac07-162">Use the following [GitBash](https://gitforwindows.org/) command to clone the .NET for Apache Spark repo to your machine.</span></span>

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="5ac07-163">撰寫適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="5ac07-163">Write a .NET for Apache Spark app</span></span>

1. <span data-ttu-id="5ac07-164">開啟 **Visual Studio**，然後巡覽至 [檔案] > [建立新專案] > [主控台應用程式 (.NET Core)]  。</span><span class="sxs-lookup"><span data-stu-id="5ac07-164">Open **Visual Studio** and navigate to **File > Create New Project > Console App (.NET Core)**.</span></span> <span data-ttu-id="5ac07-165">將應用程式命名為 **HelloSpark**。</span><span class="sxs-lookup"><span data-stu-id="5ac07-165">Name the application **HelloSpark**.</span></span>

2. <span data-ttu-id="5ac07-166">安裝 [Microsoft.Spark NuGet 套件](https://www.nuget.org/profiles/spark)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-166">Install the [Microsoft.Spark NuGet package](https://www.nuget.org/profiles/spark).</span></span> <span data-ttu-id="5ac07-167">如需安裝 NuGet 套件的詳細資訊，請參閱[安裝 NuGet 套件的不同方式](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package)。</span><span class="sxs-lookup"><span data-stu-id="5ac07-167">For more information on installing NuGet packages, see [Different ways to install a NuGet Package](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span></span>

3. <span data-ttu-id="5ac07-168">在 [方案總管]  中開啟 **Program.cs**，然後撰寫下列 C# 程式碼：</span><span class="sxs-lookup"><span data-stu-id="5ac07-168">In **Solution Explorer**, open **Program.cs** and write the following C# code:</span></span>

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. <span data-ttu-id="5ac07-169">建置方案。</span><span class="sxs-lookup"><span data-stu-id="5ac07-169">Build the solution.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="5ac07-170">執行適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="5ac07-170">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="5ac07-171">開啟 **PowerShell**，將目錄變更成您應用程式的儲存資料夾。</span><span class="sxs-lookup"><span data-stu-id="5ac07-171">Open **PowerShell** and change the directory to the folder where your app is stored.</span></span>

   ```powershell
   cd <your-app-output-directory>
   ```

2. <span data-ttu-id="5ac07-172">建立名為 **people.json** 的檔案，並在其中包含以下內容：</span><span class="sxs-lookup"><span data-stu-id="5ac07-172">Create a file called **people.json** with the following content:</span></span>

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. <span data-ttu-id="5ac07-173">使用下列 PowerShell 命令執行您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="5ac07-173">Use the following PowerShell command to run your app:</span></span>

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

<span data-ttu-id="5ac07-174">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="5ac07-174">Congratulations!</span></span> <span data-ttu-id="5ac07-175">您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ac07-175">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ac07-176">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5ac07-176">Next steps</span></span>

<span data-ttu-id="5ac07-177">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="5ac07-177">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5ac07-178">為適用於 Apache Spark 的 .NET 準備您的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="5ac07-178">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="5ac07-179">下載 **Microsoft.Spark.Worker**</span><span class="sxs-lookup"><span data-stu-id="5ac07-179">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="5ac07-180">建置及執行適用於 Apache Spark 的 .NET 簡單應用程式</span><span class="sxs-lookup"><span data-stu-id="5ac07-180">Build and run a simple .NET for Apache Spark application</span></span>

<span data-ttu-id="5ac07-181">若要深入了解，請查看資源頁面。</span><span class="sxs-lookup"><span data-stu-id="5ac07-181">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5ac07-182">適用於 Apache Spark 的 .NET 資源</span><span class="sxs-lookup"><span data-stu-id="5ac07-182">.NET for Apache Spark Resources</span></span>](../resources/index.md)
