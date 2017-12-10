---
title: "F# 開發環境功能"
description: "了解 F # 中支援的 Visual Studio 2012 的功能。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 809e9a34-b271-4c87-8356-2426b44f4721
ms.openlocfilehash: 05727bf11eccfd64f823dd280b1a19210815ca5a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="visual-f-development-environment-features"></a>Visual F# 開發環境功能

> [!NOTE]
這篇文章不是最新的 Visual Studio 中的最新狀態。  將會更新。

本主題包含 F # 中支援 Visual Studio 2012 的功能的相關資訊。

## <a name="project-features"></a>專案功能
下表摘要說明在 F # 專案中使用的範本。 如需專案和項目範本的詳細資訊，請參閱[NIB 從範本建立專案](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)。

|範本類型|描述|支援的範本|
|-------------|-----------|-------------------|
|專案範本|類型的專案中可用**新專案** 對話方塊。|<ul><li>F # 應用程式<br /></li><li>F # 程式庫<br /></li><li>F # 教學課程<br /></li><li>F # 可攜式程式庫<br /></li><ul/>|
|項目範本|檔案類型中可用**加入新項目** 對話方塊。|<ul><li>F # 原始程式檔 (.fs)<br /></li><li>F # 指令碼 (.fsx)<br /></li><li>F # 簽章檔案 (.fsi)<br /></li><li>組態檔 (.config)<br /></li><li>SQL 資料庫連接 （LINQ 到 SQL 型別提供者）<br /></li><li>SQL 資料庫連接 (LINQ to Entities 型別提供者)<br /></li><li>OData 服務連接 （LINQ 型別提供者）<br /></li><li>WSDL 服務連接 （型別提供者）<br /></li><li>XML 檔案 (.xml)<br /></li><li>文字檔<br /></li><ul/>|
若要建立可以當做獨立的可執行檔執行的應用程式，選擇 F # 應用程式專案類型。 若要建立文件庫 (也就是 managed 組件或。DLL 檔案） 用於 Windows 桌面平台上，選擇 F # 程式庫。 若要建立可攜式程式庫可以使用任何支援的平台上，選擇 F # 可攜式程式庫。 F # 可攜式程式庫專案會參考適用於建立適用於 Windows 市集應用程式，.NET Framework 4.5、 Xamarin.iOS 和 Xamarin.Android 等平台執行的應用程式的 F # 程式庫 FSharp.Core.dll 的版本。

如需資料存取的項目範本的詳細資訊，請參閱[型別提供者](../tutorials/type-providers/index.md)。

下表摘要說明支援和不支援 F # 中的專案屬性功能。 如需詳細資訊，請參閱[設定專案](configuring-projects.md)和[專案設計工具簡介](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)。

|專案設定|F # 支援的嗎？|備註|
|---------------|----------------|-----|
|資源檔|是||
|建置、 偵錯和參考設定|是||
|多目標|是||
|圖示和資訊清單|否|可透過編譯器命令列選項。|
|ASP.NET 用戶端服務|否||
|ClickOnce|否|如果適用的話，使用另一種.NET Framework 語言，用戶端專案。|
|強式命名|否|可透過編譯器命令列選項。|
|組件發行 」 和 「 版本控制|否||
|程式碼分析|否|程式碼分析工具可手動或建置後命令的一部分執行。|
|安全性 （變更信任層級）|否||

## <a name="code-and-text-editor-features"></a>程式碼和文字編輯器功能
在 F # 支援 Visual Studiocode 和文字編輯器的下列功能。 如需編輯 Visual Studio 中，與功能的文字編輯器中的程式碼的一般資訊，請參閱[程式碼和文字編輯器中撰寫程式碼](/visualstudio/ide/writing-code-in-the-code-and-text-editor)。

|功能|描述|F # 支援的嗎？|
|-------|-----------|----------------|
|自動註解|可讓您註解或取消註解的程式碼區段。|是|
|自動格式化|使用標準的縮排和樣式重新格式化程式碼。|否|
|書籤|可讓您在編輯器中儲存的位置。|是|
|變更縮排|縮排或 unindents 所選的行。|是|
|[尋找和取代文字](/visualstudio/ide/finding-and-replacing-text)|可讓您搜尋檔案、 專案或方案，而且可能要更換文字。|是|
|移至.NET Framework 應用程式開發介面的定義|當游標位於上.NET Framework API，則會顯示從.NET Framework 中繼資料產生的程式碼。|否|
|移至使用者定義應用程式開發介面的定義|當游標位於程式實體的定義，將游標移至您的程式碼中定義實體位置上。|是|
|移至行|可讓您移至特定行中的檔案、 行號。|是|
|在檔案最上方導覽列|可讓您跳到程式碼中的位置，例如，函式名稱。|是|
|大綱 請參閱[大綱](/visualstudio/ide/outlining)。|可讓您摺疊程式碼來建立更簡潔的檢視區段。|是|
|空白鍵轉定位鍵|將空格轉換成定位點。|是|
|輸入顏色標示|顯示特殊的色彩中定義的型別名稱。|是|
|快速尋找。 快速尋找、 尋找和取代 視窗，請參閱。|可讓您搜尋的檔案或專案中。|是|

## <a name="intellisense-features"></a>IntelliSense 功能
下表摘要說明支援和不支援 F # 中的 IntelliSense 功能。 一般 IntelliSense 的詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。

|功能|描述|F # 支援的嗎？|
|-------|-----------|----------------|
|自動實作的介面|會產生介面方法的程式碼片段。|否|
|程式碼片段|將常用的程式碼建構的程式庫程式碼插入至主題。|否|
|自動完成文字|輸入完成文字和名稱，如您所輸入的儲存。|是|
|使用第一個完成模式|啟用時，會選取第一個相符項目，當您輸入時，不會等待您選取其中一個，或按下文字完成**CTRL + 空格鍵**。|否|
|產生程式碼項目|可讓您產生的各種建構的虛設常式程式碼。|否|
|列出成員|當您輸入成員存取運算子 （.） 時，顯示類型的成員。|是|
|組織 Using/開啟|將所參考的命名空間組織**使用**C# 中的陳述式或**開啟**F # 中的指示詞。|否|
|參數資訊|當您輸入函式呼叫會顯示參數的相關實用資訊。|是|
|快速諮詢|顯示程式碼中的任何識別項的完整宣告。|是|
Visual Studio 2012 中不支援重構的 F # 程式碼。

## <a name="debugging-features"></a>偵錯功能
下表摘要說明當您偵錯 F # 程式碼時可用的功能。 如需 Visual Studio 偵錯工具的一般資訊，請參閱[Visual Studio 偵錯](https://msdn.microsoft.com/library/sc65sadd.aspx)。

|功能|描述|F # 支援的嗎？|
|-------|-----------|----------------|
|自動變數視窗|顯示自動或暫存變數。|否|
|中斷點|可讓您暫停在偵錯的程式碼執行的特定時間點。|是|
|條件式中斷點|啟用測試條件，可判斷是否應該暫停執行的中斷點。|是|
|編輯後繼續|可讓修改及編譯，因為您不需停止和重新啟動偵錯工具偵錯正在執行的程式碼。|否|
|運算式評估工具|評估，並在執行階段中執行的程式碼。|否，但 C# 運算式評估工具可以使用，但您必須使用 C# 語法。|
|歷程偵錯|可讓您逐步執行先前執行的程式碼。|是|
|[區域變數] 視窗|顯示在本機定義的值和變數。|是|
|執行至游標處|可讓您執行程式碼，直到達到包含游標的那一行。|是|
|逐步執行|可讓您繼續執行，並將移到所有函式呼叫。|是|
|不進入函式|可讓您繼續執行目前的堆疊框架中，並跳過任何函式呼叫。|是|

## <a name="additional-tools"></a>其他工具
下表摘要說明支援 F # 中的 Visual Studio tools。

|工具|描述|F # 支援的嗎？|
|----|-----------|----------------|
|呼叫階層|顯示在程式碼中呼叫函式的巢狀的結構。|否|
|程式碼度量|收集有關您的程式碼行計數等資訊。|否|
|類別檢視|提供類型為基礎的專案中的程式碼檢視。|否|
|[錯誤清單視窗](/visualstudio/ide/reference/error-list-window)|在程式碼中會顯示錯誤清單。|是|
|[F# Interactive](../tutorials/fsharp-interactive/index.md)|可讓您輸入 （或複製和貼上） F # 程式碼以及它立即執行，與您專案的建置無關。 F # Interactive 視窗是讀取、 評估、 列印迴圈 (REPL)。|是|
|物件瀏覽器|可讓您檢視組件中的類型。|F # 類型出現在已編譯的組件不會出現完全依照您撰寫它們。 您可以瀏覽的編譯表示 F # 型別，但您無法檢視的類型，顯示從 F #。|
|[輸出視窗](/visualstudio/ide/reference/output-window)|顯示組建輸出。|是|
|效能分析|提供工具來測量程式碼的效能。|是|
|屬性視窗|顯示並讓您編輯的物件擁有焦點的開發環境中的屬性。|是|
|[伺服器總管](https://msdn.microsoft.com/library/x603htbk.aspx)|提供方法來與各種不同的伺服器資源互動。|是|
|方案總管|可讓您檢視及管理專案和檔案。|是|
|工作清單|可讓您管理您的程式碼相關的工作項目。|是|
|測試專案|提供功能，可協助您測試您的程式碼。|否|
|工具箱|顯示含有可拖曳的物件，例如控制項和區段的文字或程式碼索引標籤。|是|

## <a name="see-also"></a>另請參閱
 [開始使用 F # Visual Studio 中](../get-started/get-started-visual-studio.md)  
 [設定專案](configuring-projects.md)  
