---
title: 開始使用 Azure 佇列儲存體使用F#
description: Azure 佇列提供可靠、 非同步傳訊應用程式元件之間。 雲端傳訊可讓您能夠單獨調整規模的應用程式元件。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 58a46dfe905a32be77a13d11df8f0544546ea0ed
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974272"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>開始使用 Azure 佇列儲存體使用 F\#

Azure 佇列儲存體提供雲端應用程式元件之間通訊。 設計應用程式進行調整，應用程式元件會經常分離，以便它們可以獨立調整。 佇列儲存體提供非同步傳訊的應用程式元件之間的通訊是否在雲端、 桌面、 在內部部署伺服器上，或在行動裝置上執行。 佇列儲存體也支援管理非同步工作並建置處理工作流程。

### <a name="about-this-tutorial"></a>關於本教學課程

本教學課程示範如何撰寫F#使用 Azure 佇列儲存體的一些常見工作的程式碼。 涵蓋的工作包括建立和刪除佇列並新增、 讀取和刪除佇列訊息。

佇列儲存體概念的概觀，請參閱[佇列儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-queues)。

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
儲存體存取金鑰也需要此帳戶。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#指令碼，然後啟動F#互動

這篇文章中的範例可以用於在F#應用程式或F#指令碼。 若要建立F#指令碼，建立的檔案`.fsx`擴充功能，例如`queues.fsx`，請在您F#開發環境。

接下來，使用[套件管理員](package-management.md)這類[Paket](https://fsprojects.github.io/Paket/)或是[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`使用指令碼中`#r`指示詞。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

新增下列`open`陳述式的`queues.fsx`檔案：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>取得連接字串

在本教學課程需要 Azure 儲存體連接字串。 如需有關連接字串的詳細資訊，請參閱 <<c0> [ 設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

教學課程中，您會輸入您的連接字串中您的指令碼，就像這樣：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

不過，這是**不建議使用**實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已遭盜用的金鑰。

實際的應用程式，來維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以這樣做：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

使用 Azure Configuration Manager 是選擇性的。 您也可以使用 API，例如.NET Framework 的`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，請使用：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

這會傳回`CloudStorageAccount`。

### <a name="create-the-queue-service-client"></a>建立佇列服務用戶端

`CloudQueueClient`類別可讓您擷取佇列儲存體中的佇列。 若要建立服務用戶端的其中一個方法如下：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

現在您已準備好撰寫程式碼來讀取資料，並將資料寫入至佇列儲存體。

## <a name="create-a-queue"></a>建立佇列

此範例示範如何建立佇列，如果不存在：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>將訊息插入佇列

若要將訊息插入現有佇列，先建立一個新`CloudQueueMessage`。 接下來，呼叫`AddMessage`方法。 A`CloudQueueMessage`可以從建立字串 （採用 utf-8 格式） 或`byte`這類陣列：

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>查看下一個訊息

您可以在查看訊息，而佇列中，而它從佇列中移除，藉由呼叫`PeekMessage`方法。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>取得下一個訊息處理

您可以藉由呼叫擷取佇列的前端處理的訊息`GetMessage`方法。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

您稍後來表示成功處理訊息使用`DeleteMessage`。

## <a name="change-the-contents-of-a-queued-message"></a>變更佇列訊息的內容

您可以變更擷取的訊息就地佇列中的內容。 如果訊息代表工作作業，您可以使用這項功能，來更新工作作業的狀態。 下列程式碼會使用新的內容更新佇列訊息，並設定延長 60 秒的可見度逾時。 這會儲存與訊息相關的工作狀態，並提供用戶端多一分鐘的時間繼續處理訊息。 您可以使用這項技術來追蹤佇列訊息上的多步驟工作流程，而不必從頭開始透過如果因為硬體或軟體失敗造成的處理步驟失敗。 一般而言，您會保留重試計數，而且如果訊息重試多個部分數次，您會將它刪除。 這可防止每次處理時就會觸發應用程式錯誤的訊息。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>下一個訊息清除佇列

您的程式碼移出佇列的訊息從佇列中兩個步驟。 當您呼叫`GetMessage`，您會取得佇列中的下一個訊息。 從傳回的訊息`GetMessage`任何從此佇列讀取訊息的程式碼。 根據預設，此訊息會保持不可見 30 秒。 若要完成從佇列移除訊息，您還必須呼叫`DeleteMessage`。 移除訊息的這兩個步驟程序可確保，如果您的程式碼無法處理訊息，因為硬體或軟體故障，您的程式碼的另一個執行個體可以取得相同訊息並再試一次。 您的程式碼呼叫`DeleteMessage`在處理訊息之後，以滑鼠右鍵。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>搭配通用佇列儲存體 Api 使用非同步工作流程

此範例會示範如何搭配通用佇列儲存體 Api 使用的非同步工作流程。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>清除佇列訊息的其他選項

有兩種方式，您可以自訂從佇列擷取訊息。
首先，您可以取得一批訊息 （最多 32 個)。 第二，您可以設定還長或短的可見度逾時，可讓您的程式碼，更多或更少時間可以完全處理每則訊息。 下列程式碼範例使用`GetMessages`取得 20 中其中一個訊息呼叫，並依序處理每則訊息。 它也會設定為 5 分鐘針對每個訊息的可見度逾時。 請注意，在 5 分鐘內啟動的所有訊息在此同時，因此後 5 分鐘傳遞從呼叫`GetMessages`，任何尚未刪除的訊息都會重新出現。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>取得佇列長度

您可以在佇列中取得的訊息數目的估計值。 `FetchAttributes`方法會要求佇列服務擷取佇列屬性，包括訊息計數。 `ApproximateMessageCount`屬性會傳回所擷取的最後一個值`FetchAttributes`方法，而不需呼叫佇列服務。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>刪除佇列

若要刪除佇列及其內含的所有訊息，請呼叫`Delete`佇列物件上的方法。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>後續步驟

既然您已了解佇列儲存體的基本概念，請遵循下列連結以深入了解更複雜的儲存體工作。

- [適用於.NET 的 azure 儲存體 Api](/dotnet/api/overview/azure/storage)
- [Azure 儲存體類型提供者](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure 儲存體團隊部落格](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體服務 REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
