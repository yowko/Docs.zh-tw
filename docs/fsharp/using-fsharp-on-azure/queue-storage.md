---
title: 以 F 開始使用 Azure 佇列儲存體#
description: Azure 佇列可在應用程式元件之間提供可靠的非同步傳訊。 雲端傳訊可讓您的應用程式元件獨立擴充。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 0ab131647e37985d45073966ffc01b9a7f379e2f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899291"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>以 F 開始使用 Azure 佇列儲存體\#

Azure 佇列儲存體可提供應用程式元件之間的雲端通訊。 設計擴充性的應用程式時，會經常分離應用程式元件，以便進行個別擴充。 佇列儲存體可針對應用程式元件間的通訊，提供非同步傳訊，無論應用程式元件是在雲端、桌面、內部部署伺服器或行動裝置上執行。 佇列儲存體也支援管理非同步工作並建置處理工作流程。

### <a name="about-this-tutorial"></a>關於本教學課程

本教學課程說明如何使用 Azure 佇列儲存體來撰寫一些常見工作的 F # 程式碼。 涵蓋的工作包括建立和刪除佇列，以及新增、讀取和刪除佇列訊息。

如需佇列儲存體的概念總覽，請參閱 [佇列儲存體的 .net 指南](/azure/storage/storage-dotnet-how-to-use-queues)。

## <a name="prerequisites"></a>先決條件

若要使用本指南，您必須先 [建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
您也需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F # 腳本並開始 F# 互動

本文中的範例可用於 F # 應用程式或 F # 腳本。 若要建立 F # 腳本，請 `.fsx` `queues.fsx` 在您的 f # 開發環境中建立副檔名為的檔案，例如。

接下來，使用 [套件管理員](package-management.md) （例如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ）， `WindowsAzure.Storage` `WindowsAzure.Storage.dll` 在您的腳本中使用指示詞安裝封裝和參考 `#r` 。

### <a name="add-namespace-declarations"></a>新增命名空間宣告

在 `queues.fsx` 檔案頂端新增下列 `open` 陳述式：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>取得您的連接字串

在本教學課程中，您將需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱 [設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

在本教學課程中，您將在腳本中輸入連接字串，如下所示：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

不過，這不 **建議** 用於實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。 如果您認為金鑰可能已遭盜用，您可以使用 Azure 入口網站重新產生金鑰。

針對實際的應用程式，維護儲存體連接字串的最佳方式是在設定檔中。 若要從設定檔提取連接字串，您可以執行下列動作：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

是否使用 Azure Configuration Manager 可由您選擇。 您也可以使用 API，例如 .NET Framework 的型別 `ConfigurationManager` 。

### <a name="parse-the-connection-string"></a>解析連接字串

若要剖析連接字串，請使用：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

這會傳回 `CloudStorageAccount` 。

### <a name="create-the-queue-service-client"></a>建立佇列服務用戶端

`CloudQueueClient`類別可讓您取出儲存在佇列儲存體中的佇列。 以下是建立服務用戶端的其中一種方式：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

您現在可以開始撰寫程式碼，以讀取佇列儲存體的資料並將資料寫入其中。

## <a name="create-a-queue"></a>建立佇列

這個範例會示範如何建立佇列（如果尚未存在）：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>將訊息插入佇列

若要將訊息插入現有佇列，請先建立新的 `CloudQueueMessage` 。 接下來，呼叫 `AddMessage` 方法。 您 `CloudQueueMessage` 可以從字串 (採用 utf-8 格式) 或陣列來建立 `byte` ，如下所示：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>查看下一個訊息

您可以藉由呼叫方法，在佇列前面查看訊息，而不需要將它從佇列中移除 `PeekMessage` 。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>取得下一個要處理的訊息

您可以藉由呼叫方法，在佇列前端取得訊息以進行處理 `GetMessage` 。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

您稍後會使用來指示訊息的成功處理 `DeleteMessage` 。

## <a name="change-the-contents-of-a-queued-message"></a>變更佇列訊息的內容

您可以在佇列中就地變更已抓取訊息的內容。 如果訊息代表工作作業，則您可以使用此功能來更新工作作業的狀態。 下列程式碼將使用新的內容更新佇列訊息，並將可見度逾時設定延長 60 秒。 這可儲存與訊息相關的工作狀態，並提供用戶端多一分鐘的時間繼續處理訊息。 您可以使用此技巧來追蹤佇列訊息上的多步驟工作流程，如果因為硬體或軟體故障而導致某個處理步驟失敗，將無需從頭開始。 通常，您也會保留重試計數，如果訊息重試次數超過數次，您就會刪除它。 這麼做可防止每次處理時便觸發應用程式錯誤的訊息。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>將下一個訊息清除佇列

您的程式碼可以使用兩個步驟將訊息自佇列中清除佇列。 當您呼叫時 `GetMessage` ，會取得佇列中的下一則訊息。 從 `GetMessage` 傳回的訊息，對於從此佇列讀取訊息的任何其他程式碼而言，將會是不可見的。 依預設，此訊息會維持 30 秒的不可見狀態。 若要完成從佇列中移除訊息，您還必須呼叫 `DeleteMessage` 。 這個移除訊息的兩步驟程序可確保您的程式碼因為硬體或軟體故障而無法處理訊息時，另一個程式碼的執行個體可以取得相同訊息並再試一次。 您的程式碼會在 `DeleteMessage` 處理完訊息之後立即呼叫。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>使用非同步工作流程搭配一般佇列儲存體 Api

此範例示範如何使用非同步工作流程搭配一般佇列儲存體 Api。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>其他將訊息移出佇列的選項

自訂從佇列中擷取訊息的方法有兩種。
首先，您可以取得一批訊息 (最多 32 個)。 其次，您可以設定較長或較短的可見度逾時，讓您的程式碼有較長或較短的時間可以完全處理每個訊息。 下列程式碼範例會使用 `GetMessages` 在一個呼叫中取得20個訊息，然後處理每個訊息。 它也會將可見度逾時設定為每個訊息五分鐘。 系統會為所有訊息同時開始5分鐘，因此在呼叫後經過5分鐘後 `GetMessages` ，任何尚未刪除的訊息都會重新顯示。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>取得佇列長度

您可以取得佇列中的估計訊息數目。 `FetchAttributes`方法會要求佇列服務取出佇列屬性，包括訊息計數。 `ApproximateMessageCount`屬性會傳回方法所取出的最後一個值 `FetchAttributes` ，而不會呼叫佇列服務。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>刪除佇列

若要刪除佇列及其內含的所有訊息，請 `Delete` 在佇列物件上呼叫方法。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>後續步驟

了解佇列儲存體的基礎概念之後，請參考下列連結以了解有關更複雜的儲存工作。

- [適用於 .NET 的 Azure 儲存體 API](/dotnet/api/overview/azure/storage)
- [Azure 儲存體型別提供者](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure 儲存體團隊部落格](/archive/blogs/windowsazurestorage/)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體服務 REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
