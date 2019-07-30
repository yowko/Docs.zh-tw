---
title: 使用 F# 開始使用 Azure 佇列儲存體
description: Azure 佇列可在應用程式元件之間提供可靠且非同步訊息。 雲端通訊可讓您的應用程式元件獨立進行調整。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 65af98fb88e91d709eb0e35907cbc2dc097634d0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630478"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>使用 F 開始使用 Azure 佇列儲存體\#

Azure 佇列儲存體提供應用程式元件之間的雲端通訊。 在設計調整的應用程式時, 應用程式元件通常會分離, 讓它們可以獨立調整。 佇列儲存體為應用程式元件之間的通訊提供非同步訊息, 不論它們是在雲端、桌面、內部部署伺服器或行動裝置上執行。 佇列儲存體也支援管理非同步工作, 以及建立處理工作流程。

### <a name="about-this-tutorial"></a>關於本教學課程

本教學課程說明如何使用F# Azure 佇列儲存體來撰寫一些常見工作的程式碼。 涵蓋的工作包括建立和刪除佇列, 以及新增、讀取和刪除佇列訊息。

如需佇列儲存體的概念總覽, 請參閱[佇列儲存體的 .net 指南](/azure/storage/storage-dotnet-how-to-use-queues)。

## <a name="prerequisites"></a>必要條件

若要使用本指南, 您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
您也需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#腳本並啟動F#互動式

本文中的範例可用於F#應用程式或F#腳本中。 若要建立F#腳本, 請在`.fsx` F#開發環境中建立`queues.fsx`副檔名為的檔案, 例如。

接下來, 使用[Paket](https://fsprojects.github.io/Paket/)或`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)之類的[套件管理員](package-management.md), 在您的腳本中`WindowsAzure.Storage.dll`使用`#r`指示詞安裝封裝和參考。

### <a name="add-namespace-declarations"></a>新增命名空間宣告

將下列`open`語句新增至檔案頂端`queues.fsx` :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>取得您的連接字串

在本教學課程中, 您將需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊, 請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

在本教學課程中, 您將在腳本中輸入連接字串, 如下所示:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

不過, 這**不建議**用於實際的專案。 您的儲存體帳戶金鑰類似于儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免將它散發給其他使用者、進行硬式編碼, 或將它儲存在其他人可以存取的純文字檔案中。 如果您認為金鑰可能遭到入侵, 您可以使用 Azure 入口網站重新產生金鑰。

對於實際的應用程式而言, 維護儲存體連接字串的最佳方式是在設定檔中。 若要從設定檔提取連接字串, 您可以執行下列動作:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

使用 Azure Configuration Manager 是選擇性的。 您也可以使用 API (例如 .NET Framework 的`ConfigurationManager`類型)。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析連接字串, 請使用:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

這會`CloudStorageAccount`傳回。

### <a name="create-the-queue-service-client"></a>建立佇列服務用戶端

`CloudQueueClient`類別可讓您取出儲存在佇列儲存體中的佇列。 以下是建立服務用戶端的其中一種方式:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

現在您已準備好撰寫程式碼, 以讀取資料並將資料寫入佇列儲存體。

## <a name="create-a-queue"></a>建立佇列

這個範例示範如何建立佇列 (如果尚未存在):

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>將訊息插入佇列中

若要將訊息插入現有佇列, 請先建立新`CloudQueueMessage`的。 接下來, 呼叫`AddMessage`方法。 可以從字串 (採用 utf-8 格式) `byte`或陣列建立, 如下所示: `CloudQueueMessage`

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>查看下一個訊息

藉由呼叫`PeekMessage`方法, 您可以在佇列前面查看訊息, 而不需將它從佇列中移除。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>取得要處理的下一個訊息

您可以藉由呼叫`GetMessage`方法來抓取佇列前端的訊息, 以進行處理。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

您稍後會使用`DeleteMessage`來指示訊息的處理成功。

## <a name="change-the-contents-of-a-queued-message"></a>變更佇列訊息的內容

您可以在佇列中就地變更抓取訊息的內容。 如果訊息代表工作工作, 您可以使用這項功能來更新工作的狀態。 下列程式碼會以新的內容更新佇列訊息, 並將可見度 timeout 設定為延長另一個60秒。 這會儲存與訊息相關聯之工作的狀態, 並讓用戶端有另一分鐘的時間繼續處理訊息。 您可以使用這項技術來追蹤佇列訊息上的多步驟工作流程, 如果因硬體或軟體失敗而導致處理步驟失敗, 則不需要從頭開始。 一般來說, 您也會保留重試計數, 如果訊息重試超過數次, 您就會刪除它。 這會針對每次處理時觸發應用程式錯誤的訊息進行保護。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>將下一個訊息取消佇列

您的程式碼會以兩個步驟將訊息從佇列中取消佇列。 當您呼叫`GetMessage`時, 您會取得佇列中的下一個訊息。 從這個佇列讀取`GetMessage`訊息的任何其他程式碼, 都不會看到從傳回的訊息。 根據預設, 此訊息會在30秒內保持不可見。 若要完成從佇列中移除訊息的作業, 您也`DeleteMessage`必須呼叫。 這個移除訊息的兩步驟程式可確保您的程式碼因為硬體或軟體故障而無法處理訊息時, 另一個程式碼實例可以取得相同的訊息, 然後再試一次。 您的程式`DeleteMessage`代碼會在處理完訊息之後立即呼叫。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>使用具有一般佇列儲存體 Api 的非同步工作流程

此範例示範如何搭配使用非同步工作流程與一般佇列儲存體 Api。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>取消佇列訊息的其他選項

有兩種方式可以自訂佇列中的訊息抓取。
首先, 您可以取得一批訊息 (最多 32)。 第二, 您可以設定較長或較短的隱藏超時, 讓您的程式碼更多或更少的時間來完整處理每個訊息。 下列程式碼範例會`GetMessages`使用在一次呼叫中取得20個訊息, 然後處理每個訊息。 它也會將每個訊息的隱藏超時設定為5分鐘。 請注意, 所有訊息的5分鐘都會啟動一次, 因此在呼叫`GetMessages`之後的5分鐘過後, 任何尚未刪除的訊息都會再次顯示。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>取得佇列長度

您可以取得佇列中的訊息數目估計。 `FetchAttributes`方法會要求佇列服務取得佇列屬性, 包括訊息計數。 屬性會傳回`FetchAttributes`方法所取得的最後一個值, 而不會呼叫佇列服務。 `ApproximateMessageCount`

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>刪除佇列

若要刪除佇列及其內含的所有訊息, 請在佇列物件`Delete`上呼叫方法。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>後續步驟

既然您已瞭解佇列儲存體的基本概念, 請遵循下列連結以瞭解更複雜的儲存工作。

- [適用于 .NET 的 Azure 儲存體 Api](/dotnet/api/overview/azure/storage)
- [Azure 儲存體型別提供者](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure 儲存體小組的 Blog](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體 Services REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
