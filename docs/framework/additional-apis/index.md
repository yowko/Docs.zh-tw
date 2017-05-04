---
title: "其他類別庫和 API | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: b53b8acc2a6c56db6a9d8a9b7c685a2d400a53e1
ms.openlocfilehash: 34815268b707aa70d174a1bbc04c32276db8412d
ms.lasthandoff: 05/02/2017

---

# <a name="additional-class-libraries-and-apis"></a>其他類別庫和 API

由於 .NET Framework 會持續演變，因此為了改善跨平台開發工作或讓客戶早點採用新功能，我們會不定期 (Out of Band，OOB) 發行新功能。 本主題列出有提供文件的 OOB 專案。  
  
除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。 例如，<xref:System.Text.CodePagesEncodingProvider> 類別會向使用 .NET Framework 開發的 UWP 應用程式提供字碼頁編碼。 本主題也會列出這些程式庫。  
  
## <a name="oob-projects"></a>OOB 專案
  
| 專案 | 描述 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | 提供具備執行緒安全且保證不會再變更其內容的集合。 |
| <xref:System.Net.Http.WinHttpHandler> | 為 <xref:System.Net.Http.HttpClient> 提供以 Windows 的 WinHTTP 介面為基礎的訊息處理常式。 |
| [System.Numerics.Vectors (英文)](https://msdn.microsoft.com/library/mt452176.aspx) | 提供可利用 SIMD 硬體加速的向量類型程式庫。| 
| <xref:System.Threading.Tasks.Dataflow> | TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。 |  

## <a name="platform-specific-libraries"></a>平台特定程式庫
  
| 專案 | 描述 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | 擴充 <xref:System.Text.EncodingProvider> 類別，來向以通用 Windows 平台為目標的應用程式提供字碼頁編碼。 |  
  
## <a name="private-apis"></a>私人 API  

這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。  
  
| API 名稱 |  
| -------- |  
| [s_isDebuggerCheckDisabledForTestPurposes 欄位](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |  
| [DataMemberFieldEditor 類別](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |  
| [DataMemberListEditor 類別](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |  
  
## <a name="see-also"></a>請參閱

[.NET Framework 和不定期發行](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

