---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: 30084143949d2243fd310448c52e6b861505ad66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191246"
---
# <a name="getcustomui"></a>GetCustomUI
如果實作時，請呼叫由 PresentationHost.exe 從主機取得自訂的進度和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>參數  
 `pwzProgressAssemblyName`  
  
 [out]指標，包含主機提供進度使用者介面的組件。  
  
 `pwzProgressClassName`  
  
 [out]最好是主機提供進度使用者介面的類別名稱[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]檔案中使用<xref:System.Windows.Controls.Page>是其最上層元素。 此類別位於所指定的組件`pwzProgressAssemblyName`。  
  
 `pwzErrorAssemblyName`  
  
 [out]指標，包含主機提供的錯誤使用者介面的組件。  
  
 `pwzErrorClassName`  
  
 [out]為主機提供的錯誤使用者的類別名稱介面，最好的 XAML 檔案<xref:System.Windows.Controls.Page>是其最上層元素。 此類別位於所指定的組件`pwzErrorAssemblyName`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:忽略。  
  
## <a name="remarks"></a>備註  
 主應用程式可能會有特定的佈景主題，PresentationHost.exe 的預設使用者介面可能不符合。 如果發生這種情況，主應用程式可實作[GetCustomUI](getcustomui.md)返回進度和錯誤的使用者介面 PresentationHost.exe。 一定會呼叫 PresentationHost.exe [GetCustomUI](getcustomui.md)之前使用其預設使用者介面。  
  
 一次在 PresentationHost 的初始化期間，會呼叫此函數。  
  
## <a name="see-also"></a>另請參閱

- [IWpfHostSupport](iwpfhostsupport.md)
