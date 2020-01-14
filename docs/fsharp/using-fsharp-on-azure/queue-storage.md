---
title: 使用 F# 開始使用 Azure 佇列儲存體
description: Azure 佇列可在應用程式元件之間提供可靠的非同步傳訊。 雲端傳訊可讓您的應用程式元件獨立擴充。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 841068ac91aecc53811359e27d984907569a2c6d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935500"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>使用 F\# 開始使用 Azure 佇列儲存體

Azure 佇列儲存體可提供應用程式元件之間的雲端傳訊。 設計擴充性的應用程式時，會經常分離應用程式元件，以便進行個別擴充。 佇列儲存體可針對應用程式元件間的通訊，提供非同步傳訊，無論應用程式元件是在雲端、桌面、內部部署伺服器或行動裝置上執行。 佇列儲存體也支援管理非同步工作並建置處理工作流程。

### <a name="about-this-tutorial"></a>關於本教學課程

本教學課程說明如何使用F# Azure 佇列儲存體來撰寫一些常見工作的程式碼。 涵蓋的工作包括建立和刪除佇列，以及新增、讀取和刪除佇列訊息。

如需佇列儲存體的概念總覽，請參閱[佇列儲存體的 .net 指南](/azure/storage/storage-dotnet-how-to-use-queues)。

## <a name="prerequisites"></a>必要條件：

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
您也需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#腳本並啟動F#互動式

本文中的範例可用於F#應用程式或F#腳本中。 若要建立F#腳本，請在您F#的開發環境中建立具有 `.fsx` 副檔名的檔案，例如 `queues.fsx`。

接下來，使用[套件管理員](package-management.md)（例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/) ），在您的腳本中使用 `#r` 指示詞來安裝 `WindowsAzure.Storage` 封裝和參考 `WindowsAzure.Storage.dll`。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

在 `queues.fsx` 檔案頂端新增下列 `open` 陳述式：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>取得您的連接字串

在本教學課程中，您將需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

在本教學課程中，您將在腳本中輸入連接字串，如下所示：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

不過，這**不建議**用於實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。 如果您認為金鑰可能遭到入侵，您可以使用 Azure 入口網站重新產生金鑰。

對於實際的應用程式而言，維護儲存體連接字串的最佳方式是在設定檔中。 若要從設定檔提取連接字串，您可以執行下列動作：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

是否使用 Azure Configuration Manager 可由您選擇。 您也可以使用 API，例如 .NET Framework 的 `ConfigurationManager` 類型。

### <a name="parse-the-connection-string"></a>解析連接字串

若要剖析連接字串，請使用：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

這會傳回 `CloudStorageAccount`。

### <a name="create-the-queue-service-client"></a>建立佇列服務用戶端

`CloudQueueClient` 類別可讓您取出儲存在佇列儲存體中的佇列。 以下是建立服務用戶端的其中一種方式：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

您現在可以開始撰寫程式碼，以讀取佇列儲存體的資料並將資料寫入其中。

## <a name="create-a-queue"></a>建立佇列

這個範例示範如何建立佇列（如果尚未存在）：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>將訊息插入佇列

若要將訊息插入現有佇列，請先建立新的 `CloudQueueMessage`。 接下來，呼叫 `AddMessage` 方法。 您可以從字串（採用 UTF-8 格式）或 `byte` 陣列建立 `CloudQueueMessage`，如下所示：

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>查看下一個訊息

藉由呼叫 `PeekMessage` 方法，您可以在佇列前面查看訊息，而不需將它從佇列中移除。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>取得要處理的下一個訊息

您可以藉由呼叫 `GetMessage` 方法，在佇列的前端抓取訊息以進行處理。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

您稍後會使用 `DeleteMessage`指出訊息的處理成功。

## <a name="change-the-contents-of-a-queued-message"></a>變更佇列訊息的內容

您可以在佇列中就地變更抓取訊息的內容。 如果訊息代表工作作業，則您可以使用此功能來更新工作作業的狀態。 下列程式碼將使用新的內容更新佇列訊息，並將可見度逾時設定延長 60 秒。 這可儲存與訊息相關的工作狀態，並提供用戶端多一分鐘的時間繼續處理訊息。 您可以使用此技巧來追蹤佇列訊息上的多步驟工作流程，如果因為硬體或軟體故障而導致某個處理步驟失敗，將無需從頭開始。 一般來說，您也會保留重試計數，如果訊息重試超過數次，您就會刪除它。 這麼做可防止每次處理時便觸發應用程式錯誤的訊息。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>將下一個訊息清除佇列

您的程式碼可以使用兩個步驟將訊息自佇列中清除佇列。 當您呼叫 `GetMessage`時，您會取得佇列中的下一個訊息。 從 `GetMessage` 傳回的訊息，對於從此佇列讀取訊息的任何其他程式碼而言，將會是不可見的。 依預設，此訊息會維持 30 秒的不可見狀態。 若要完成從佇列中移除訊息的作業，您也必須呼叫 `DeleteMessage`。 這個移除訊息的兩步驟程序可確保您的程式碼因為硬體或軟體故障而無法處理訊息時，另一個程式碼的執行個體可以取得相同訊息並再試一次。 在處理訊息之後，您的程式碼會立即呼叫 `DeleteMessage`。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>使用具有一般佇列儲存體 Api 的非同步工作流程

此範例示範如何搭配使用非同步工作流程與一般佇列儲存體 Api。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>其他將訊息移出佇列的選項

自訂從佇列中擷取訊息的方法有兩種。
首先，您可以取得一批訊息 (最多 32 個)。 其次，您可以設定較長或較短的可見度逾時，讓您的程式碼有較長或較短的時間可以完全處理每個訊息。 下列程式碼範例會使用 `GetMessages` 在一次呼叫中取得20個訊息，然後處理每個訊息。 它也會將可見度逾時設定為每個訊息五分鐘。 請注意，5分鐘會同時啟動所有訊息，因此從呼叫 `GetMessages`之後，經過5分鐘後，任何尚未刪除的訊息都會再次顯示。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>取得佇列長度

您可以取得佇列中的估計訊息數目。 `FetchAttributes` 方法會要求佇列服務取得佇列屬性，包括訊息計數。 `ApproximateMessageCount` 屬性會傳回 `FetchAttributes` 方法所取得的最後一個值，而不會呼叫佇列服務。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>刪除佇列

若要刪除佇列及其內含的所有訊息，請在佇列物件上呼叫 `Delete` 方法。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>後續步驟

了解佇列儲存體的基礎概念之後，請參考下列連結以了解有關更複雜的儲存工作。

- [適用於 .NET 的 Azure 儲存體 API](/dotnet/api/overview/azure/storage)
- [Azure 儲存體型別提供者](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure 儲存體團隊部落格](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體服務 REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
