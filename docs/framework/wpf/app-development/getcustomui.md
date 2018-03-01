---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 88c2873a5929e25335b0c6ef64f8121e31177ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getcustomui"></a>GetCustomUI
如果實作，呼叫 PresentationHost.exe 從主機上，取得自訂的進度和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a>參數  
 `pwzProgressAssemblyName`  
  
 [out]指標，包含主機提供進度使用者介面的組件。  
  
 `pwzProgressClassName`  
  
 [out]最好是主機提供進度使用者介面、 類別名稱[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]檔案搭配<xref:System.Windows.Controls.Page>是其最上層元素。 這個類別位於所指定的組件`pwzProgressAssemblyName`。  
  
 `pwzErrorAssemblyName`  
  
 [out]指標，包含主機提供的錯誤使用者介面的組件。  
  
 `pwzErrorClassName`  
  
 [out]為主機提供的錯誤使用者類別的名稱介面，最好是使用 XAML 檔案<xref:System.Windows.Controls.Page>是其最上層元素。 這個類別位於所指定的組件`pwzErrorAssemblyName`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT： 忽略。  
  
## <a name="remarks"></a>備註  
 主應用程式可能 PresentationHost.exe 的預設使用者介面可能不符合特定主題。 如果這種情況，主應用程式可以實作[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)回到進度和錯誤的使用者介面 PresentationHost.exe。 一定會呼叫 PresentationHost.exe [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)才能使用其預設使用者介面。  
  
 一次 PresentationHost 的初始化期間，會呼叫此函式。  
  
## <a name="see-also"></a>請參閱  
 [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
