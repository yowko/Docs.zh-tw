---
title: 在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET
description: 瞭解如何在 Azure HDInsight 的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: ff6b3a64c01fb9148d3abe3d04579233d11a4f73
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599651"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET

本文會教您如何在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET。 您可以透過命令列和 Azure 入口網站的組合，在 Azure HDInsight 叢集上部署 Apache Spark 的 .NET (如需詳細資訊，請參閱 [如何將適用于 Apache Spark 的 .net 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)) ，但筆記本提供更具互動性和反復的體驗。

Azure HDInsight 叢集已經隨附 Jupyter 筆記本，所以您只需要設定 Jupyter 筆記本來執行 .NET 以進行 Apache Spark。 若要在 Jupyter 筆記本中使用 .NET 進行 Apache Spark，需要有 c # 的複寫功能，以逐行執行您的 c # 程式碼，並在必要時保留執行狀態。 [試用 .net](https://github.com/dotnet/try) 已整合為正式的 .net 複寫。

若要透過 Jupyter 筆記本體驗來啟用 .NET 以進行 Apache Spark，您必須遵循幾個手動步驟來 [Ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) 和提交 HDInsight Spark 叢集上的 [腳本動作](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) 。

> [!NOTE]
> 這項功能是 *實驗* 性的，且不受 HDInsight Spark 團隊的支援。

## <a name="prerequisites"></a>必要條件

如果您還沒有帳戶，請建立一個 [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) 叢集。

1. 造訪 [Azure 入口網站](https://portal.azure.com) ，然後選取 [ **+ 建立資源**]。

1. 建立新的 Azure HDInsight 叢集資源。 在叢集建立期間選取 **Spark 2.4** 和 **HDI 4.0** 。

## <a name="install-net-for-apache-spark"></a>安裝適用于 Apache Spark 的 .NET

在 [Azure 入口網站中，選取您在上一個步驟中建立的 **HDInsight Spark** 叢集。

### <a name="stop-the-livy-server"></a>停止 Livy 伺服器

1. 從入口網站中，選取 **[總覽**]，然後選取 [ **Ambari 首頁**]。 如果出現提示，請輸入叢集的登入認證。

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-ambari.png)

2. 從左側導覽功能表中選取 [ **Spark2** ]，然後選取 [ **LIVY FOR Spark2 SERVER**]。

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-livyserver.png)

3. 選取 **hn0 .。。主機**。

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-host.png)

4. 選取 **Livy For Spark2 Server** 旁的省略號，然後選取 [ **停止**]。 出現提示時，請選取 **[確定]** 以繼續。

   停止 Spark2 伺服器的 Livy。
   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/stop-server.png)

5. 針對 hn1 重複上述步驟 ... **主機**。

### <a name="submit-an-hdinsight-script-action"></a>提交 HDInsight 腳本動作

1. `install-interactive-notebook.sh`是安裝 .net 進行 Apache Spark 的腳本，並會變更 Apache Livy 和 sparkmagic。 將腳本動作提交至 HDInsight 之前，您必須先建立並上傳 `install-interactive-notebook.sh` 。

   在您的本機電腦上建立名為 **install-interactive-notebook.sh** 的新檔案，並貼上 [install-interactive-notebook.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)的內容。

   將腳本上傳至可從 HDInsight 叢集存取的 [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) 。 例如： `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh` 。

2. 使用 [HDInsight 指令碼動作](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)在叢集上執行 `install-interactive-notebook.sh`。

   返回 Azure 入口網站中的 HDI 叢集，然後從左邊的選項中選取 [ **腳本動作** ]。 您可以提交一個腳本動作，在您的 HDInsight Spark 叢集上部署 Apache Spark 的 .NET 複寫。 套用下列設定：

   |屬性  |描述  |
   |---------|---------|
   | 指令碼類型 | 自訂 |
   | 名稱 | *安裝適用于 Apache Spark 互動式筆記本體驗的 .NET* |
   | Bash 指令碼 URI | 您上傳 `install-interactive-notebook.sh` 的目標 URI。 |
   | 節點類型| Head 和背景工作 |
   | 參數 | 適用于 Apache Spark 版本的 .NET。 您可以檢查 [.net 的 Apache Spark 版本](https://github.com/dotnet/spark/releases)。 例如，如果您想要安裝 Sparkdotnet 1.0.0 版，則會是 `1.0.0` 。

   當腳本動作的狀態旁邊出現綠色核取記號時，移至下一個步驟。

### <a name="start-the-livy-server"></a>啟動 Livy 伺服器

遵循 [Stop Livy server](#stop-the-livy-server) 一節中的指示， **開始** (而不是 **停止**) 適用于主機的 Spark2 伺服器 **hn0** 和 **hn1** 的 Livy。

### <a name="set-up-spark-default-configurations"></a>設定 Spark 預設設定

1. 從入口網站中，選取 **[總覽**]，然後選取 [ **Ambari 首頁**]。 出現提示時，輸入叢集的叢集登入認證。

2. 選取 **Spark2** [Spark2 **] 和 [** 進行]。 然後，選取 [ **自訂 spark2-預設值**]。

   ![設定設定](./media/hdinsight-notebook-installation/spark-configs.png)

3. 選取 [ **新增屬性** ]，以新增 Spark 預設設定。

   ![新增屬性](./media/hdinsight-notebook-installation/add-property.png)

   有三個個別的屬性。 使用單一屬性加入模式中的 **TEXT** 屬性類型，一次加入一個專案。 檢查任何索引鍵/值之前或之後都沒有任何額外的空格。

   * **屬性1**
       * 關鍵：&ensp;&ensp;`spark.dotnet.shell.command`
       * 值：`/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **屬性 2** 使用您在上一個腳本動作中包含 Apache Spark 的 .NET 版本。
       * 關鍵：&ensp;&ensp;`spark.dotnet.packages`
       * 值：`["nuget: Microsoft.Spark, 1.0.0", "nuget: Microsoft.Spark.Extensions.Delta, 1.0.0"]`

   * **屬性3**
       * 關鍵：&ensp;&ensp;`spark.dotnet.interpreter`
       * 值：`try`

   例如，下圖會捕獲新增屬性1的設定：

   ![設定設定](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   加入三個屬性之後，請選取 [ **儲存**]。 如果您看到設定建議的警告畫面，請選取 [ **仍要繼續**]。

4. 重新開機受影響的元件。

   加入新的屬性之後，您必須重新開機受變更影響的元件。 在頂端，選取 [ **重新開機**]，然後從下拉式清單中 **重新開機所有受影響** 的。

   ![設定設定](./media/hdinsight-notebook-installation/restart-affected.png)

   出現提示時，選取 [ **確認全部重新開機** ] 以繼續，然後按一下 **[確定** ] 以完成。

## <a name="submit-jobs-through-a-jupyter-notebook"></a>透過 Jupyter Notebook 提交作業

完成上述步驟之後，您現在可以透過 Jupyter 筆記本提交適用于 Apache Spark 作業的 .NET。

1. 為 Apache Spark 筆記本建立新的 .NET。 從 Azure 入口網站的 HDI 叢集中啟動 Jupyter Notebook。

   ![啟動 Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   然後，選取 [**新增**  >  **.net Spark (c # )** 以建立筆記本。

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. 使用 .NET 提交 Apache Spark 的作業。

   使用下列程式碼片段來建立資料框架：

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![提交 Spark 作業](./media/hdinsight-notebook-installation/create-df.png)

   使用下列程式碼片段，將使用者定義函式註冊 (UDF) ，並使用 UDF 搭配資料框架：

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![提交 Spark 作業](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>後續步驟

* [將 .NET for Apache Spark 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [HDInsight 檔](/azure/hdinsight/)
