---
title: '開始使用 Azure 佇列儲存體使用 F #'
description: Azure 佇列提供可靠、 非同步應用程式元件之間的訊息。 雲端訊息可讓您獨立擴充的應用程式元件。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 14bbc657f965fc262d2a83b1fdf982fe5e75d55e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569410"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>開始使用 Azure 佇列儲存體使用 F # #

Azure 佇列儲存體提供雲端應用程式元件之間的傳訊。 在設計應用程式的小數位數時，應用程式元件通常分開處理，以便它們可以獨立擴充。 佇列儲存體提供非同步傳訊應用程式元件之間的通訊是否在雲端中，在桌面上，在內部部署伺服器上，或行動裝置上執行。 佇列儲存體也支援管理非同步工作，以及建置程序工作流程。

### <a name="about-this-tutorial"></a>關於本教學課程

本教學課程會示範如何撰寫使用 Azure 佇列儲存體的一些常見工作的 F # 程式碼。 涵蓋的工作包括建立和刪除佇列並新增、 讀取和刪除佇列訊息。

佇列儲存體概念的概觀，請參閱[佇列儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-queues)。

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
您還需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F # 指令碼，並開始 F # Interactive

這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。 若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`queues.fsx`，F # 開發環境中。

接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`指令碼使用`#r`指示詞。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

加入下列`open`上方的陳述式`queues.fsx`檔案：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>取得連接字串

此教學課程中，您將需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

教學課程中，您會輸入您的連接字串中指令碼中，像這樣：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

不過，這是**不建議**用於真實的專案。 儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。 一律為保護您的儲存體帳戶金鑰，請小心。 避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。

用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

使用 Azure 組態管理員是選擇性的。 您也可以使用例如.NET Framework API`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，使用：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

這會傳回`CloudStorageAccount`。

### <a name="create-the-queue-service-client"></a>建立佇列服務用戶端

`CloudQueueClient`類別可讓您擷取儲存在佇列儲存體中的佇列。 以下是如何建立服務用戶端：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

現在您已準備好開始撰寫程式碼讀取資料，並將資料寫入至佇列儲存體。

## <a name="create-a-queue"></a>建立佇列

這個範例示範如何建立佇列，如果不存在：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>將訊息插入佇列

若要將訊息插入現有佇列，先建立新`CloudQueueMessage`。 接下來，呼叫`AddMessage`方法。 A`CloudQueueMessage`可以從其中建立格式的字串 （utf-8） 或`byte`陣列，像這樣：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>查看下一個訊息

而不移除它藉由呼叫從佇列查看訊息佇列中，前端`PeekMessage`方法。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>取得下一個訊息處理

您可以藉由呼叫擷取的訊息在處理佇列的前端`GetMessage`方法。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

您稍後使用來表示成功處理訊息`DeleteMessage`。

## <a name="change-the-contents-of-a-queued-message"></a>變更佇列的訊息的內容

您可以變更擷取的訊息就地佇列中的內容。 如果訊息代表的工作，您可以使用這項功能，來更新 「 工作 」 工作的狀態。 下列程式碼會更新新的內容，佇列訊息，並設定以擴充另一個 60 秒的可見度逾時。 這樣會節省與訊息相關聯的工作的狀態，並繼續處理訊息的另一個分鐘讓用戶端。 您可以使用這項技術，來追蹤訊息排入佇列，而不必從頭開始處理步驟失敗，因為硬體或軟體失敗時多步驟工作流程。 一般而言，您會保留重試計數，而且如果一些次數超過重試的訊息，則會刪除它。 這可防止每次處理時就會觸發應用程式錯誤的訊息。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>清除佇列的下一個訊息

您的程式碼會將佇列佇列將訊息從佇列中兩個步驟。 當您呼叫`GetMessage`，您可以取得下一個訊息佇列中。 傳回訊息`GetMessage`變成看不到任何其他從此佇列讀取訊息的程式碼。 根據預設，此訊息會保持可見 30 秒。 若要完成從佇列移除訊息，您必須也呼叫`DeleteMessage`。 這兩個步驟的程序中移除訊息可確保，如果您的程式碼無法處理訊息，因為硬體或軟體失敗，另一個執行個體的程式碼可以取得相同的訊息並再試一次。 您的程式碼呼叫`DeleteMessage`處理訊息之後，以滑鼠右鍵。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>使用一般佇列儲存體 Api 使用非同步工作流程

這個範例會示範如何使用一般佇列儲存體 Api 使用非同步工作流程。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>取消佇列訊息的其他選項

有兩種方式，您可以自訂從佇列擷取訊息。
首先，您可以取得一批訊息 （最多 32)。 接下來，您可以設定長或短過了隱藏逾時，可讓您的程式碼，更多或更少的時間來完整處理每個訊息。 下列程式碼範例使用`GetMessages`取得 20 中其中一個訊息呼叫然後再處理每個訊息。 它也會針對每個訊息的五分鐘設定過了隱藏逾時。 請注意，在 5 分鐘內啟動的所有訊息在相同的時間，因此之後 5 分鐘的時間已過呼叫`GetMessages`，任何已被刪除的訊息一次將變成可見。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>取得佇列長度

您可以在佇列中取得估計的訊息數目。 `FetchAttributes`方法會要求佇列服務擷取佇列的屬性，包括訊息計數。 `ApproximateMessageCount`屬性會傳回所擷取的最後一個值`FetchAttributes`方法，而不需要呼叫佇列服務。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>刪除佇列

若要刪除佇列與在它所包含的所有訊息，請呼叫`Delete`上的佇列物件的方法。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>後續步驟

既然您已經學會佇列儲存體的基本概念，請遵循下列連結，以了解更複雜的儲存體工作。

- [適用於.NET 的 azure 儲存體 Api](/dotnet/api/overview/azure/storage)
- [Azure 儲存體型別提供者](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure 儲存體團隊部落格](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體服務 REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
