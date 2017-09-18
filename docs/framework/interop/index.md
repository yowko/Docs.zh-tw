---
title: "與 Unmanaged 程式碼互通"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ff86b062efddde6f97555efb97247f60a6e1db98
ms.contentlocale: zh-tw
ms.lasthandoff: 09/18/2017

---
# <a name="interoperating-with-unmanaged-code"></a>與 Unmanaged 程式碼互通
.NET Framework 可促進與 COM 元件、COM+ 服務、外部型別程式庫和許多作業系統服務進行的互動。 資料類型、方法簽章和錯誤處理機制因 Managed 和 Unmanaged 物件模型而有所不同。 為了簡化 .NET Framework 元件與 Unmanaged 程式碼之間的互通性，以及簡化移轉路徑，通用語言執行平台會對用戶端與伺服器隱匿這些物件模型中的差異。  
  
 在執行階段的控制之下執行的程式碼稱為 Managed 程式碼。 相反地，在執行階段外部執行的程式碼稱為 Unmanaged 程式碼。 COM 元件、ActiveX 介面及 Win32 API 函式都是 Unmanaged 程式碼的範例。  
  
## <a name="in-this-section"></a>本章節內容  
 [與 Unmanaged 程式碼交互操作的「如何」主題](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 提供概念文件中所有與 Unmanaged 程式碼交互操作之「如何」主題的連結。  
  
 [將 COM 元件公開給 .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 描述如何從 .NET Framework 應用程式使用 COM 元件。  
  
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 描述如何從 COM 應用程式使用 .NET Framework 元件。  
  
 [使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 描述如何使用平台叫用呼叫 Unmanaged DLL 函式。  
  
 [交互操作的設計考量](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 提供撰寫整合式 COM 元件的秘訣。  
  
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)  
 描述適用於 COM Interop 和平台叫用的封送處理。  
  
 [操作說明：對應 HRESULT 和例外狀況](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 描述例外狀況與 HRESULT 之間的對應。  
  
 [使用泛型型別交互操作](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 描述泛型型別在 COM Interop 中使用時的行為。  
  
## <a name="related-sections"></a>相關章節  
 [進階 COM 互通性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 提供有關將 COM 元件納入 .NET Framework 應用程式的詳細資訊連結。

