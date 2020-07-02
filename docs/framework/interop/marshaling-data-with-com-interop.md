---
title: 使用 COM Interop 封送處理資料
description: 請參閱涵蓋以 COM Interop 封送處理資料的文章。 Tlbimp.exe 和 Tlbexp.exe 工具會在 COM 類型程式庫和 interop 元件之間進行轉換。
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: eedfb60a75e2fe5fafdaa786dbb54adddf28400e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621505"
---
# <a name="marshaling-data-with-com-interop"></a>使用 COM Interop 封送處理資料
COM Interop 同時提供使用來自 Managed 程式碼之 COM 物件的支援和公開 Managed 物件給 COM 的支援。 廣泛支援封送處理資料至 COM 或對來自 COM 的資料封送處理，幾乎一律會提供正確的封送處理行為。  
  
 Windows SDK 包含下列 COM Interop 工具：  
  
- [型別程式庫匯入工具 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)，這會將 COM 型別程式庫轉換成 Interop 組件。 從這個組件中，Interop 封送處理服務會產生包裝函式，在 Managed 和 Unmanaged 記憶體之間執行資料封送處理。  
  
- [型別程式庫匯出工具 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)，這會從組件產生 COM 型別程式庫，並產生在方法呼叫期間執行封送處理的包裝函式。  
  
 下列各節會連結到各個主題，以描述當您可以 (或必須) 提供具有其他類型資訊的封送處理器時，自訂 Interop 包裝函式的程序。  
  
## <a name="in-this-section"></a>本節內容  
[如何：手動建立包裝](how-to-create-wrappers-manually.md)函式描述如何在 managed 原始程式碼中手動建立 COM 包裝函式。

 [作法：將受控碼 DCOM 移轉至 WCF](how-to-migrate-managed-code-dcom-to-wcf.md)  
 描述如何將受控的 DCOM 程式碼移轉至 WCF 的最安全解決方案。  
  
## <a name="related-sections"></a>相關章節  
 [COM 資料類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 提供對應的 Managed 和 Unmanaged 資料類型。  
  
 [自訂 COM 可呼叫包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 描述如何在設計階段使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性明確封送處理資料類型。  
  
 [自訂執行階段可呼叫包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 描述如何調整 Interop 組件中的類型封送處理行為，以及描述如何以手動方式定義 COM 類型。  
  
 [進階 COM 互通性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 提供有關將 COM 元件納入 .NET Framework 應用程式的詳細資訊連結。  
  
 [組件至型別程式庫轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 描述組件至類型程式庫匯出轉換的程序。  
  
 [型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 描述類型程式庫至組件匯入轉換的程序。  
  
 [使用泛型型別交互操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 描述使用泛型類型來取得 COM 互通性時所支援的動作。
