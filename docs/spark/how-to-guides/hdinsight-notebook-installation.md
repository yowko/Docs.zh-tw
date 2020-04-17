---
title: 在 Azure HDInsight Spark 群集上的 Jupyter 筆記型電腦上安裝用於 Apache Spark 的 NET
description: 瞭解如何在 Azure HDInsight 的 Jupyter 筆記本上安裝用於 Apache Spark 的 .NET。
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 953bffe5f6ec56cd0adf4224afd2eedfe0001aa9
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607411"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>在 Azure HDInsight Spark 群集上的 Jupyter 筆記型電腦上安裝用於 Apache Spark 的 NET

本文教您如何在 Azure HDInsight Spark 群集上的 Jupyter 筆記型電腦上安裝用於 Apache Spark 的 .NET。 您可以透過命令列和 Azure 門戶的組合在 Azure HDInsight 群集上部署 A奇星(有關詳細資訊,請參閱[如何將 .NET 用於 Apache Spark 的應用程式部署到 Azure HDInsight),](../tutorials/hdinsight-deployment.md)但筆記本可提供更具互動性和反覆運算性的體驗。

Azure HDInsight 群集已經附帶了 Jupyter 筆記本,因此您所要做的就是將 Jupyter 筆記本配置為運行的 .NET 以用於 Apache Spark。 要在 Jupyter 筆記本中使用用於 Apache Spark 的 .NET,需要 C# REPL 逐行執行 C# 代碼,並在必要時保留執行狀態。 [try .NET](https://github.com/dotnet/try)已集成為官方 .NET REPL。

要透過 Jupyter 筆記本體驗啟用 .NET 阿帕契火花,您需要在[Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari)中執行幾個手動步驟,並在 HDInsight Spark 群集上提交[文稿操作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)。

> [!NOTE]
> 此功能是*實驗性*的,HDInsight Spark 團隊不支援此功能。

## <a name="prerequisites"></a>必要條件

如果還沒有,請創建[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight)群集。

1. 訪問[Azure 門戶](https://portal.azure.com)並選擇 **「創建資源**」。

1. 創建新的 Azure HDInsight 群集資源。 在群集創建期間選擇**Spark 2.4**和**HDI 4.0。**

## <a name="install-net-for-apache-spark"></a>安裝 .NET 用於阿帕奇火花

在 Azure 門戶中,選擇您在上一步中建立的**HDInsight Spark 叢集**。

### <a name="stop-the-livy-server"></a>停止利維伺服器

1. 從門戶中,選擇 **「概述**」,然後選擇**Ambari 首頁**。 如果出現提示,請輸入群集的登錄憑據。

   ![停止利維伺服器](./media/hdinsight-notebook-installation/select-ambari.png)

2. 從左側導航選單中選擇**Spark2,** 然後選擇**SPARK2 伺服器的 LIVY。**

   ![停止利維伺服器](./media/hdinsight-notebook-installation/select-livyserver.png)

3. 選擇**hn0...主機**。

   ![停止利維伺服器](./media/hdinsight-notebook-installation/select-host.png)

4. 為**Spark2 伺服器選擇 Livy**旁邊的省略號,然後選擇 **"停止**"。 當出現提示時,選擇 **「確定**」以繼續。

   停止Spark2伺服器的利維。
   ![停止利維伺服器](./media/hdinsight-notebook-installation/stop-server.png)

5. 重複**hn1 的上述步驟...主機**。

### <a name="submit-an-hdinsight-script-action"></a>提交 HDInsight 文稿操作

1. 是`install-interactive-notebook.sh`一個腳本,安裝 .NET 為 Apache Spark,並作出更改阿帕奇利維和火花魔術。 在將文稿操作到 HDInsight 之前,您需要建立和上`install-interactive-notebook.sh`載 。

   在本地電腦中建立名為**install-interactive-notebook.sh**的新檔案,並貼上[install-interactive-notebook.sh 內容的內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)。

   將文本上傳到可從 HDInsight 群集訪問的[URI。](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) 例如： `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh` 。

2. 使用 [HDInsight 指令碼動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)在叢集上執行 `install-interactive-notebook.sh`。

   傳回 Azure 門戶中的 HDI 叢集,並從左側的選項中選擇**文稿操作**。 提交一個腳本操作以在 HDInsight Spark 群集上部署 Apache Spark REPL 的 .NET。 套用下列設定：

   |屬性  |描述  |
   |---------|---------|
   | 指令碼類型 | Custom |
   | 名稱 | *安裝 .NET,用於 Apache Spark 互動式筆記本體驗* |
   | Bash 指令碼 URI | 您上傳 `install-interactive-notebook.sh` 的目標 URI。 |
   | 節點類型| 頭部和工人 |
   | 參數 | 阿帕奇火花版本的 .NET。 您可以檢查[.NET 的阿帕契火花版本](https://github.com/dotnet/spark/releases)。 例如,如果要安裝 Sparkdotnet 版本 0.6.0,`0.6.0`則它將是 。

   當綠色複選標記顯示在腳本操作的狀態旁邊時,將移動到下一步。

### <a name="start-the-livy-server"></a>開機維伺服器

按照[停止利維伺服器](#stop-the-livy-server)部分**的說明開始(** 而不是**停止**)主機**hn0**和**hn1**的 Spark2 伺服器的 Livy。

### <a name="set-up-spark-default-configurations"></a>設定 Spark 預設設定

1. 從門戶中,選擇 **「概述**」,然後選擇**Ambari 首頁**。 出現提示時，輸入叢集的叢集登入認證。

2. 選擇**Spark2**與**CONFIGS**。 然後,選擇**自訂 spark2 預設值**。

   ![設定設定](./media/hdinsight-notebook-installation/spark-configs.png)

3. 選擇 **"添加屬性..."** 以添加 Spark 默認設置。

   ![新增屬性](./media/hdinsight-notebook-installation/add-property.png)

   有三個單獨的屬性。 在 Single 屬性添加模式下使用**TEXT**屬性類型一次添加一個。 檢查在任意鍵/值之前或之後沒有任何額外的空格。

   * **屬性 1**
       * 關鍵:&ensp;&ensp;`spark.dotnet.shell.command`
       * 值: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **屬性 2**使用上一個腳本操作中包含的 Apache Spark 的 .NET 版本。
       * 關鍵:&ensp;&ensp;`spark.dotnet.packages`
       * 值: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **屬性 3**
       * 關鍵:&ensp;&ensp;`spark.dotnet.interpreter`
       * 值: `try`

   例如,下圖擷取用於新增屬性 1 的設定:

   ![設定設定](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   添加三個屬性後,選擇 **"保存**"。 如果您看到配置建議的警告螢幕,請選擇 **"執行"。**

4. 重新啟動受影響的元件。

   添加新屬性後,需要重新啟動受更改影響的元件。 在頂部,選擇**RESTART**,然後從下拉**清單中重新啟動所有受影響的。**

   ![設定設定](./media/hdinsight-notebook-installation/restart-affected.png)

   當提示時,選擇 **「確認全部」** 以繼續,然後單擊 **「確定**」以完成。

## <a name="submit-jobs-through-a-jupyter-notebook"></a>通過聚居筆記本提交作業

完成上述步驟后,您現在可以通過 Jupyter 筆記本提交用於 Apache Spark 作業的 .NET。

1. 為 Apache Spark 筆記本創建新的 .NET。 從 Azure 門戶中的 HDI 群集啟動 Jupyter 筆記本。

   ![啟動朱彼特筆記本](./media/hdinsight-notebook-installation/launch-notebook.png)

   然後,選擇**新建** > **.NET Spark (C#)** 以創建筆記本。

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. 使用 .NET 為 Apache Spark 提交作業。

   使用以下代碼段建立資料的格格:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![提交火花作業](./media/hdinsight-notebook-installation/create-df.png)

   使用以下代碼段註冊使用者定義的函數 (UDF), 並將 UDF 與 DataFrame 一起使用:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![提交火花作業](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>後續步驟

* [將 .NET for Apache Spark 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [HDInsight 文件](https://docs.microsoft.com/azure/hdinsight/)
