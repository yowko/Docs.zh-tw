---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005705"
---
# <a name="getcustomui"></a>GetCustomUI
由 Presentationhost.exe 呼叫，以從主機取得自訂進度和錯誤訊息（如果已執行）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>參數  
 `pwzProgressAssemblyName`  
  
 脫銷元件的指標，其中包含主機提供的進度使用者介面。  
  
 `pwzProgressClassName`  
  
 脫銷屬於主機提供的進度使用者介面的類別名稱，最好是具有 <xref:System.Windows.Controls.Page> 的 XAML 檔案是其最上層元素。 這個類別位於 `pwzProgressAssemblyName` 所指定的元件中。  
  
 `pwzErrorAssemblyName`  
  
 脫銷包含主機提供的錯誤使用者介面之元件的指標。  
  
 `pwzErrorClassName`  
  
 脫銷屬於主機提供的錯誤使用者介面之類別的名稱，最好是具有 <xref:System.Windows.Controls.Page> 的 XAML 檔案是其最上層元素。 這個類別位於 `pwzErrorAssemblyName` 所指定的元件中。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:忽略。  
  
## <a name="remarks"></a>備註  
 主應用程式可能有特定主題，Presentationhost.exe .exe 的預設使用者介面可能不符合。 如果是這種情況，主應用程式可以執行[GetCustomUI](getcustomui.md) ，將進度和錯誤使用者介面傳回 presentationhost.exe。 Presentationhost.exe 在使用其預設的使用者介面之前，一律會呼叫[GetCustomUI](getcustomui.md) 。  
  
 在 Presentationhost.exe 的初始化期間，會呼叫這個函式一次。  
  
## <a name="see-also"></a>另請參閱

- [IWpfHostSupport](iwpfhostsupport.md)
