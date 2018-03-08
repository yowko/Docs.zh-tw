---
title: "處理 COM Interop 例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e894d07e77b929b1ea22df2d34e542544ec3b1f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="handling-com-interop-exceptions"></a>處理 COM Interop 例外狀況
Managed 和 Unmanaged 程式碼可一起運作來處理例外狀況。 如果方法在 Managed 程式碼擲回例外狀況，則 Common Language Runtime 可以傳遞 HRESULT 給 COM 物件。 如果在 Unmanaged 程式碼中的方法藉由傳回失敗 HRESULT 而失敗，則執行階段會擲回 Managed 程式碼可以攔截的例外狀況。  
  
 執行階段會自動將 HRESULT 從 COM Interop 對應至更特定的例外狀況。 例如，E_ACCESSDENIED 會變成 <xref:System.UnauthorizedAccessException>，而 E_OUTOFMEMORY 變成 <xref:System.OutOfMemoryException> 等等。  
  
 如果 HRESULT 是自訂的結果，或者它對於執行階段是未知的，則執行階段會傳遞泛型 <xref:System.Runtime.InteropServices.COMException> 給用戶端。 **COMException** 的 **ErrorCode** 屬性包含 HRESULT 值。  
  
## <a name="working-with-ierrorinfo"></a>使用 IErrorInfo  
 當錯誤從 COM 傳遞至 Managed 程式碼時，執行階段會填入錯誤資訊至例外狀況物件。 支援 IErrorInfo 且傳回 HRESULT 的 COM 物件會提供這項資訊給 Managed 程式碼例外狀況。 例如，執行階段從 COM 錯誤對應描述至例外狀況的 <xref:System.Exception.Message%2A> 屬性。 如果 HRESULT 沒有提供其他錯誤資訊，則執行階段會填滿預設值到許多例外狀況的屬性。  
  
 如果在 Unmanaged 程式碼中的方法失敗，則例外狀況可以傳遞至 Managed 程式碼區段。 本主題 [HRESULT 和例外狀況](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)包含一個表格，顯示 HRESULT 如何對應至執行階段例外狀況物件。  

## <a name="see-also"></a>請參閱
[例外狀況](index.md) 
