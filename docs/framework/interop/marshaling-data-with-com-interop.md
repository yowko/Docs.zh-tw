---
title: "使用 COM Interop 封送處理資料"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2af80ddb558959171c255a61fae460729306e0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-data-with-com-interop"></a>使用 COM Interop 封送處理資料
COM Interop 同時提供使用來自 Managed 程式碼之 COM 物件的支援和公開 Managed 物件給 COM 的支援。 廣泛支援封送處理資料至 COM 或對來自 COM 的資料封送處理，幾乎一律會提供正確的封送處理行為。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 包含下列的 COM Interop 工具：  
  
-   [型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)，這會將 COM 型別程式庫轉換成 Interop 組件。 從這個組件中，Interop 封送處理服務會產生包裝函式，在 Managed 和 Unmanaged 記憶體之間執行資料封送處理。  
  
-   [型別程式庫匯出工具 (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)，這會從組件產生 COM 型別程式庫，並產生在方法呼叫期間執行封送處理的包裝函式。  
  
 下列各節將說明您可以 （或必須） 提供具有其他類型資訊的封送處理器時，自訂 interop 包裝函式的處理程序的主題連結。  
  
## <a name="in-this-section"></a>本節內容  
[如何： 手動建立包裝函式](how-to-create-wrappers-manually.md)   
描述如何在 managed 的原始程式碼中手動建立 COM 包裝函式。 
 
 [如何：將 Managed 程式碼 DCOM 移轉至 WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 描述如何將 managed 的 DCOM 程式碼移轉至 WCF 的最安全的解決方案。  
  
## <a name="related-sections"></a>相關章節  
 [COM 資料類型](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)  
 提供對應的 Managed 和 Unmanaged 資料類型。  
  
 [自訂 COM 可呼叫包裝函式](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)  
 描述如何明確封送處理資料型別使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>在設計階段屬性。  
  
 [自訂執行階段可呼叫包裝函式](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)  
 描述如何調整 Interop 組件中的類型封送處理行為，以及描述如何以手動方式定義 COM 類型。  
  
 [進階 COM 互通性](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)  
 提供有關將 COM 元件納入 .NET Framework 應用程式的詳細資訊連結。  
  
 [組件至型別程式庫轉換的摘要](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)  
 描述組件至類型程式庫匯出轉換的程序。  
  
 [型別程式庫至組件轉換的摘要](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)  
 描述類型程式庫至組件匯入轉換的程序。  
  
 [使用泛型型別互通](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)  
 描述使用泛型類型來取得 COM 互通性時所支援的動作。
