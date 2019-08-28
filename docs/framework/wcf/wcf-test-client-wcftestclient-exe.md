---
title: WCF 測試用戶端 (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: e637a2bb26bd0cc4bea653155c2a85ef5af19fd9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038357"
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF 測試用戶端 (WcfTestClient.exe)
Windows Communication Foundation (WCF) 測試用戶端 (WcfTestClient) 是一種 GUI 工具, 可讓使用者輸入測試參數、將該輸入提交至服務, 以及查看服務傳回的回應。 結合 WCF 服務主機時, 它提供了順暢的服務測試體驗。

您通常可以在下列位置找到 WCF 測試用戶端 (WcfTestClient): `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` -「社區」可能是「企業」、「專業」或「社區」的其中一個, 視安裝的 Visual Studio 層級而定。

## <a name="scenarios-for-using-test-client"></a>使用測試用戶端的案例

下列各節討論最常見的案例, 您可以使用 WCF 測試用戶端來簡化您的開發流程。

### <a name="inside-visual-studio"></a>在 Visual Studio 內部

#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>WCF 服務主機啟動具有單一服務的 WCF 測試用戶端

在您建立新的 WCF 服務專案並按下 F5 啟動偵錯工具之後, WCF 服務主機就會開始在您的專案中裝載服務。 然後, WCF 測試用戶端會開啟並顯示在設定檔案中定義的服務端點清單。 您可以測試參數並叫用服務，然後重複這個程序以持續測試及驗證服務。

#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>WCF 服務主機啟動具有多個服務的 WCF 測試用戶端

您也可以使用 WCF 測試用戶端, 協助您對包含多個服務的服務專案進行 debug。 當 WCF 測試用戶端開啟時, 它會自動逐一查看專案中的服務清單, 並開啟它們進行測試。

### <a name="outside-visual-studio"></a>在 Visual Studio 外部

您也可以叫用 Visual Studio 外部的 WCF 測試用戶端 (WcfTestClient), 以在網際網路上測試任意服務。 若要找出該工具，請移至下列位置：

`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE`(其中的「社區」可以是「企業」、「專業」或「社區」的其中一個, 視電腦上安裝的 Visual Studio 層級而定)

若要使用該工具，按兩下檔名即可從這個位置開啟，或者是從命令列進行啟動。

WCF 測試用戶端會接受任意數目的 Uri 做為命令列引數。  這些引數是可以測試的服務 URI。

`wcfTestClient.exe URI1 URI2 …`

在 [WCF 測試用戶端] 視窗開啟之後 ->, 按一下 [檔案] [**新增服務**], 然後輸入您想要開啟之服務的端點位址。

## <a name="wcf-test-client-user-interface"></a>WCF 測試用戶端使用者介面

您可以搭配單一服務或多個服務使用 WCF 測試用戶端。

### <a name="service-operations"></a>服務作業

[WCF 測試用戶端] 主視窗的左窗格會列出所有可用的服務, 以及其各自的端點和作業。

按兩下某項作業時，您可以在右窗格中具有該作業名稱的新索引標籤內，檢視其內容。

左窗格還會列出用戶端組態檔。 按兩下任何項目，即可在右窗格中新出現的索引視窗上看見檔案的內容。

### <a name="entering-test-parameters"></a>輸入測試參數

若要檢視測試參數，請按兩下作業，在右窗格中開啟它。 根據預設, 參數會顯示在**格式化**視圖中, 您可以為參數輸入任意值來測試服務。

若要查看訊息的 XML, 請按一下 [ **xml**]。 若要將它們傳送至服務,請按一下 [叫用]。

針對資料集參數, 按一下 [ **...** ] 按鈕, 位於 [**編輯**] 旁 。 若要在顯示 DataGrid 的新視窗中編輯它。 請注意 [**複製資料集**] 和 [**貼上資料集**] 按鈕的外觀。 如果在第一次編輯時 DataSet 物件的結構描述為未知，DataGrid 為空白。 您必須將具有相同結構描述的 DataSet 物件貼入 DataGrid 中的目前物件 (請注意，您必須在貼上作業前從其他地方複製結構描述)。您也可以按一下 [**複製資料集**] 按鈕, 以複製資料集物件供未來使用。

服務的回應會出現在測試參數下方。

> [!NOTE]
> 如果預期的傳回值是字串，則結果會顯示為引號括住的字串，即使提供的輸入並未以引號括住。

如果您在建立服務合約時將特定作業指定為單向，就不會顯示任何服務回應。 訊息一旦排入佇列中準備傳遞，快顯對話方塊就會出現，通知您已成功傳送訊息。

### <a name="session-support"></a>工作階段支援

服務作業的索引標籤中的 [**啟動新 proxy** ] 核取方塊, 可讓您切換會話支援。 這個方塊預設為清除。

當您針對特定作業 (或是相同服務端點中的其他作業) 輸入測試參數, 並按一下 [多次叫用] 核取方塊時, 這些作業會共用一個 proxy, 而服務狀態會保存在多個業務.

如果已核取 [**啟動新 proxy** ] 核取方塊, 則會針對每個叫用新的 proxy, 先前的會話案例會結束, 且服務狀態會是 [重設]。

### <a name="editing-client-configuration"></a>編輯用戶端組態

[WCF 測試用戶端] 主視窗的左窗格會列出用戶端設定檔案。 按兩下任何項目，即可在右窗格中顯示檔案的內容。

#### <a name="edit-with-service-configuration-editor"></a>使用服務組態編輯器進行編輯

以滑鼠右鍵按一下左窗格中的 [**設定檔**], 然後選取內容功能表 [**以 svcconfigeditor.exe 編輯**]。 服務組態編輯器隨即啟動，並顯示用戶端組態內容。 您可以在該工具內編輯組態並進行儲存。

在 [服務設定編輯器] 中儲存檔案之後, WCF 測試用戶端會顯示一則警告訊息, 告知您檔案已在外部修改, 並詢問您是否要重載該檔案。

如果您選取 [**是]** , [Client. .dll .config] 索引標籤中的設定內容就會反映您在編輯器中所做的變更。

如果您選取 [**否**], 則 [Client .dll .config] 索引標籤中的設定內容會維持不變, 而且修改後的內容會自動儲存至來源檔案。

#### <a name="restore-to-default-configuration"></a>還原至預設組態

如果您想要取消所有變更並還原為預設用戶端設定, 請以滑鼠右鍵按一下左窗格中的 [**設定檔**], 然後選取內容功能表 [**還原為預設**設定]。預設的設定值已載入, 且會還原 [Client .dll .config] 索引標籤中的內容。

#### <a name="validate-changes"></a>驗證變更

在 WCF 測試用戶端中載入儲存的變更時, 會檢查設定是否符合 WCF 架構的有效性。 如果發現錯誤，會顯示對話方塊說明錯誤詳細資料。

在 proxy 產生、二進位編譯或服務叫用期間, 支援編輯的功能表項目 (也就是「編輯 ...」、「還原 ...」等等) 都會停用。 將更新的設定載入至 WCF 測試用戶端時, 也會停用服務調用。

#### <a name="persist-client-configuration"></a>保存用戶端組態

[**工具**->] [**選項**->] [**用戶端**設定] 索引標籤包含 [**啟動服務時永遠重新**產生設定] 選項 (預設為啟用)。 此選項指定每次 WCF 測試用戶端載入服務時, 它會根據最新的服務合約和服務 App.config 檔案重新產生設定檔。

如果您已編輯 WCF 服務的用戶端設定, 而且想要一律使用這個更新過的檔案來進行服務的偵錯工具, 您可以取消選取 [**重新**產生] 選項。 如此一來, 即使您更新服務並重新開啟 WCF 測試用戶端, 也是您先前更新的檔案, 而不是根據更新的服務重新產生的檔案。

但是，您可能需要編輯組態檔，讓其跟重新產生的 Proxy 一致。 如果重新產生的 Proxy 和組態檔因更新服務而不相符，則在叫用服務時將發生錯誤。

> [!CAUTION]
> 如果您修改過用戶端組態檔並選擇供往後重複使用，則可以在下列位置找到該檔案：
>
> \Documents 和設定\\[使用者帳戶] \My Documents\Test 用戶端專案。
>
> 任何儲存在用戶端組態檔中經過更新的認證資訊，皆受到這個資料夾的存取控制清單 (ACL) 所保護。

### <a name="adding-removing-and-refreshing-services"></a>新增、移除和重新整理服務

#### <a name="add-service"></a>新增服務

按一下 [檔案] [**新增服務**], 將服務新增至 WCF 測試用戶端。 -> 接著會要求您輸入要新增之服務的 URI (端點位址)。 服務位址可以是 Mex 位址或 WSDL 位址。

您也可以在 [**最近使用的服務**] 子功能表中, 找到10個最近新增的服務端點清單。 如果您選取其中一個, 則會將指定的服務加入至 WCF 測試用戶端。

您也可以用滑鼠右鍵按一下服務樹狀目錄 [**我的服務專案**] 的根, 然後選取 [**新增服務**] 來達到相同的結果。

在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援新增服務的功能表項目。 同時也會停用服務叫用。

#### <a name="remove-service"></a>移除服務

以滑鼠右鍵按一下要移除之服務的服務根目錄, 然後選取 [**移除服務**], 從 WCF 測試用戶端移除服務。

在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援移除服務的功能表項目。 同時也會停用服務叫用。

#### <a name="refresh-service"></a>重新整理服務

如果在執行 WCF 測試用戶端時對服務進行變更, 而您想要確保該服務的 WCF 測試用戶端執行是最新的, 請以滑鼠右鍵按一下服務的服務根目錄, 然後選取 [重新整理**服務**]。 請注意，重新整理後會重設服務狀態。

在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援重新整理服務的功能表項目。 同時也會停用服務叫用。

## <a name="location-of-files-generated-by-the-test-client"></a>測試用戶端產生的檔案位置

根據預設, WCF 測試用戶端會將產生的用戶端程式代碼和設定檔儲存在 "%appdata%\Local\temp\Test Client Projects" 資料夾中。 在 WCF 測試用戶端結束之後, 會刪除這個資料夾。 如果在 WCF 測試用戶端中修改設定檔, 而且停用 [**啟動服務時永遠重新**產生設定] 選項, 則會將修改過的檔案複製到 "My Documents\Test Client Projects" 下具有對應的 "CachedConfig" 資料夾中 (中繼資料-位址到檔案名稱) XML 檔案做為索引。

您也可以在命令列中啟動 WCF 測試用戶端, 使用`/ProjectPath`參數指定新的所需路徑來儲存產生的檔案, 或`/RestoreProjectPath`使用參數來還原預設位置。 語法如下：

`wcfTestClient.exe /ProjectPath [desired location]`

執行此命令並不會開啟 WCF 測試用戶端。 只是會變更資料夾位置。 您可以執行此命令, 確定 WCF 測試用戶端是否正在執行。 重新開機 WCF 測試用戶端時, 會套用新的位置。 位置資訊可以儲存在登錄中, 或在 [%appdata%\Local\temp\Test 用戶端專案] 資料夾的 WcfTestClient 檔案中。

## <a name="features-supported-by-wcf-test-client"></a>WCF 測試用戶端支援的功能

以下是 WCF 測試用戶端支援的功能清單:

- 服務引動過程：要求/回覆和單向訊息。

- 繫結：Svcutil.exe 支援的所有繫結。

- 控制工作階段。

- 訊息合約。

- XML 序列化。

以下是 WCF 測試用戶端不支援的功能清單:

- 型別：<xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的型別，包括相關 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性、<xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 型別，以及 ADO.NET <xref:System.Data.DataTable> 型別。

- 雙工合約。

- 異動。

- 安全性：CardSpace、憑證和使用者名稱/密碼。

- 繫結：WSFederationbinding、任何內容系結和 Https 系結、WebHttpbinding (Json 回應訊息支援)。

## <a name="closing-wcf-test-client"></a>關閉 WCF 測試用戶端

您可以透過下列方式關閉 WCF 測試用戶端:

- 在 **[檔案]** 功能表上按一下 **[結束]** 。 或者, 在 [WCF 測試用戶端] 主視窗中, 按一下 [**關閉**]。 這兩個動作也會關閉 WCF 服務自動裝載, 並在 Visual Studio 啟動 WCF 測試用戶端時, 停止 Visual Studio 的偵錯工具。

- 以滑鼠右鍵按一下通知區域中的 [ **WCF 服務主機**] 圖示, 然後按一下 [結束] **。** 這會關閉 WCF 服務自動裝載和 WCF 測試用戶端, 並停止 Visual Studio 的偵錯工具。

## <a name="see-also"></a>另請參閱

- [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
