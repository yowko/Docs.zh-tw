---
title: 在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET
description: 瞭解如何在 Azure HDInsight 的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617739"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET

本文會教您如何在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET。 您可以透過命令列和 Azure 入口網站的組合，在 Azure HDInsight 叢集上部署 Apache Spark 的 .NET （如需詳細資訊，請參閱[如何將適用于 Apache Spark 應用程式的 .net 部署至 Azure HDInsight](../tutorials/hdinsight-deployment.md)），但筆記本提供更具互動性和反復的體驗。

Azure HDInsight 叢集已隨附于 Jupyter 筆記本，因此您只需要設定 Jupyter 筆記本來執行適用于 Apache Spark 的 .NET。 若要在 Jupyter 筆記本中使用 .NET for Apache Spark，需要進行 c # 複寫以逐行執行 c # 程式碼，並在必要時保留執行狀態。 [試用 .net](https://github.com/dotnet/try)已整合為官方的 .net 複寫。

若要透過 Jupyter 筆記本體驗啟用 .NET for Apache Spark，您需要遵循幾個手動步驟，透過[Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari)並在 HDInsight Spark 叢集上提交[腳本動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)。

> [!NOTE]
> 這項功能是*實驗*性，而且 HDInsight Spark 小組不支援。

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>必要條件

如果您還沒有帳戶，請建立一個[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight)叢集。

1. 流覽[Azure 入口網站](https://portal.azure.com)，然後選取 [ **+ 建立資源**]。

1. 建立新的 Azure HDInsight 叢集資源。 在叢集建立期間選取 [ **Spark 2.4**和**HDI 4.0** ]。

## <a name="install-net-for-apache-spark"></a>安裝適用于 Apache Spark 的 .NET

在 [Azure 入口網站中，選取您在上一個步驟中建立的**HDInsight Spark**叢集。

### <a name="stop-the-livy-server"></a>停止 Livy 伺服器

1. 在入口網站中，選取 **[總覽**]，然後選取 [ **Ambari home**]。 如果出現提示，請輸入叢集的登入認證。

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-ambari.png)

2. 從左側導覽功能表中選取 [ **Spark2** ]，然後選取 [ **LIVY FOR Spark2 SERVER**]。

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-livyserver.png)

3. 選取 [ **hn0]主機**。

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-host.png)

4. 選取 [ **Livy For Spark2 Server** ] 旁的省略號，然後選取 [**停止**]。 出現提示時，選取 **[確定]** 以繼續。

   停止 Spark2 伺服器的 Livy。
   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/stop-server.png)

5. 針對 [hn1] 重複上述步驟 ... **主機**。

### <a name="submit-an-hdinsight-script-action"></a>提交 HDInsight 腳本動作

1. `install-interactive-notebook.sh`是安裝 .net 進行 Apache Spark 的腳本，並會變更 Apache Livy 和 sparkmagic。 將腳本動作提交至 HDInsight 之前，您必須先建立並上傳 `install-interactive-notebook.sh` 。

   在您的本機電腦上建立名為**install-interactive-notebook.sh**的新檔案，並貼上[install-interactive-notebook.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)的內容。

   將腳本上傳至可從 HDInsight 叢集存取的[URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) 。 例如 `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`。

2. 使用 [HDInsight 指令碼動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)在叢集上執行 `install-interactive-notebook.sh`。

   返回 Azure 入口網站中的 HDI 叢集，然後從左邊的選項中選取 [**腳本動作**]。 您提交一個腳本動作，在 HDInsight Spark 叢集上部署適用于 Apache Spark 複寫的 .NET。 套用下列設定：

   |屬性  |描述  |
   |---------|---------|
   | 指令碼類型 | 自訂 |
   | 名稱 | *安裝適用于 Apache Spark 互動式筆記本體驗的 .NET* |
   | Bash 指令碼 URI | 您上傳 `install-interactive-notebook.sh` 的目標 URI。 |
   | 節點類型| 前端和背景工作角色 |
   | 參數 | 適用于 Apache Spark 版本的 .NET。 您可以檢查[.net 的 Apache Spark 版本](https://github.com/dotnet/spark/releases)。 例如，如果您想要安裝 Sparkdotnet 版本0.6.0，則會是 `0.6.0` 。

   當腳本動作的狀態旁邊出現綠色核取記號時，移至下一個步驟。

### <a name="start-the-livy-server"></a>啟動 Livy 伺服器

遵循[停止 Livy 伺服器](#stop-the-livy-server)一節中的指示，**開始**（而不是**停止**）適用于主機的 Livy for Spark2 伺服器**hn0**和**hn1**。

### <a name="set-up-spark-default-configurations"></a>設定 Spark 預設設定

1. 在入口網站中，選取 **[總覽**]，然後選取 [ **Ambari home**]。 出現提示時，輸入叢集的叢集登入認證。

2. 選取**Spark2** [Spark2**和 [** 進行]]。 然後選取 [**自訂 spark2-預設值**]。

   ![設定配置](./media/hdinsight-notebook-installation/spark-configs.png)

3. 選取 [**新增屬性**]，以新增 Spark 預設設定。

   ![新增屬性](./media/hdinsight-notebook-installation/add-property.png)

   有三個個別的屬性。 使用 [單一屬性] [新增模式] 中的 [ **TEXT** ] 屬性類型，一次新增一個。 檢查任何索引鍵/值前後是否有任何多餘的空格。

   * **屬性1**
       * 擊鍵&ensp;&ensp;`spark.dotnet.shell.command`
       * 值: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **屬性 2**使用您在上一個腳本動作中包含的 Apache Spark .NET 版本。
       * 擊鍵&ensp;&ensp;`spark.dotnet.packages`
       * 值: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **屬性3**
       * 擊鍵&ensp;&ensp;`spark.dotnet.interpreter`
       * 值: `try`

   例如，下圖會捕捉新增屬性1的設定：

   ![設定配置](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   新增三個屬性後，選取 [**儲存**]。 如果您看到設定建議的警告畫面，請選取 [**無論如何繼續**]。

4. 重新開機受影響的元件。

   加入新的屬性之後，您必須重新開機受變更影響的元件。 在頂端，選取 [**重新開機**]，然後從下拉式選單 [**重新開機所有受影響**的]。

   ![設定配置](./media/hdinsight-notebook-installation/restart-affected.png)

   出現提示時，選取 [**確認全部重新開機**以繼續]，然後按一下 **[確定**] 以完成。

## <a name="submit-jobs-through-a-jupyter-notebook"></a>透過 Jupyter 筆記本提交作業

完成先前的步驟之後，您現在可以透過 Jupyter 筆記本提交您的 .NET 以進行 Apache Spark 作業。

1. 為 Apache Spark 筆記本建立新的 .NET。 在 Azure 入口網站中，從您的 HDI 叢集啟動 Jupyter 筆記本。

   ![啟動 Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   然後，選取**New**  >  **[新增 .net Spark （c #）** ] 以建立筆記本。

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. 使用適用于 Apache Spark 的 .NET 提交作業。

   使用下列程式碼片段來建立資料框架：

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![提交 Spark 作業](./media/hdinsight-notebook-installation/create-df.png)

   使用下列程式碼片段來註冊使用者定義函式（UDF），並搭配資料框架使用 UDF：

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![提交 Spark 作業](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>後續步驟

* [將 .NET for Apache Spark 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [HDInsight 檔](https://docs.microsoft.com/azure/hdinsight/)
