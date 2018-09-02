---
title: 進階格式選取
ms.date: 03/30/2017
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
ms.openlocfilehash: e5c396ce22e9021d453a70f3826b0bd3cc6aaf42
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466619"
---
# <a name="advanced-format-selection"></a>進階格式選取
此範例示範如何擴充 Windows Communication Foundation (WCF) REST 程式設計模型，以支援新的傳出回應格式。 此外，這個範例使用 T4 範本將回應當做 XHTML 頁面傳回，示範如何實作檢視樣式程式設計模型。  
  
## <a name="sample-details"></a>範例詳細資料  
 這個範例包含一項簡單的服務，以及可對服務發出要求的用戶端程式碼。  服務支援單一 [WebGet] 作業，這項作業擁有下面這個方法簽章：`Message EchoListWithGet(string list);`  
  
 當用戶端對服務發出要求時，它會從 `list` 查詢字串參數提供逗號分隔的項目清單，而服務會以下列其中一種格式傳回同一份清單：XML、JSON、Atom、XHTML 或 jpeg。  
  
 服務傳回的回應格式會先以 `format` 查詢字串參數決定，再以隨要求提供的 HTTP Accept 標頭決定。 如果 `format` 查詢字串參數的值是上面其中一種格式，則回應會以該格式傳回。 如果 `format` 查詢字串不存在，則服務會從要求逐一查看 Accept 標頭項目，然後傳回服務支援的第一個 content-type 的格式。  
  
 值得注意的是作業的傳回型別。 WCF REST 程式設計模型原本就僅支援 XML 和 JSON 的回應格式，當作業傳回型別以外<xref:System.ServiceModel.Channels.Message>。 不過，使用 <xref:System.ServiceModel.Channels.Message> 做為傳回類型時，開發人員可以完全掌控應如何格式化訊息的內容。  
  
 這個範例使用 <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>、<xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> 和 <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> 方法分別將字串清單序列化為 XML、JSON 和 ATOM 訊息。 若為 jpeg 回應格式，則會使用 <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> 方法，且影像會儲存到資料流。 若為 XHTML 回應，則會使用 <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> 搭配預先處理的 T4 範本，這個範本是由 .tt 檔和自動產生的 .cs 檔所組成。 .tt 檔可讓開發人員以包含變數和控制項結構的範本形式撰寫回應。 如需 T4 的詳細資訊，請參閱[藉由使用文字範本產生成品](https://go.microsoft.com/fwlink/?LinkId=166023)。  
  
 此範例包含在主控台應用程式中執行的自我裝載服務和用戶端。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-run-this-sample"></a>若要執行這個範例  
  
1.  開啟「進階格式選取範例」的方案。 啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您應該以系統管理員身分執行，才能讓範例成功執行。 執行這項操作，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]圖示，然後選擇**系統管理員身分執行**從內容功能表。  
  
2.  按下 CTRL+SHIFT+B 建置方案，然後按下 Ctrl-F5，在不偵錯的情況下執行主控台應用程式 AdvancedFormatSelection 專案。 主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。  
  
3.  當範例執行時，用戶端會對服務傳送要求，然後將回應寫入至主控台視窗。 請注意不同格式的回應：XML、JSON、Atom 和 XHTML。  
  
4.  接著會提示您瀏覽至 URI，您可以在其中要求 .jpeg 格式的回應。 開啟瀏覽器並瀏覽至指定的 URI。  
  
5.  按下任何按鍵可終止此範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>另請參閱
