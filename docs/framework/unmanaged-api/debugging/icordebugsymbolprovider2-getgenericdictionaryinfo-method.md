---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo 方法
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c69be53a429e2f40741cc1e4c20fef3b7363654
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2::GetGenericDictionaryInfo 方法
擷取泛型字典對應。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppMemoryBuffer`  
 [out]位址指標[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)物件，其中包含泛型字典對應。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
 對應是由兩個最上層區段所組成：  
  
-   A[目錄](#Directory)包含此對應中所有字典的相對虛擬位址 (RVA)。  
  
-   位元組對齊[堆積](#Heap)，其中包含物件具現化資訊。 會在最後一個目錄項目之後立即啟動。  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>目錄  
 目錄中的每個項目是指堆積中的位移，也就是相對於堆積開頭的位移。 個別項目的值不一定是唯一的，可能會有多個目錄項目指向堆積中的同一個位移。  
  
 泛型字典對應的目錄部分具有下列結構：  
  
-   前 4 個位元組包含字典項目數 (也就是字典中的相對虛擬位址數目)。 我們將這個值為*N*。如果設定高位元，項目會依相對虛擬位址的遞增順序排序。  
  
-   *N*遵循目錄項目。 每個項目是由兩個 4 位元組區段中的 8 個位元組所組成：  
  
    -   位元組 0-3：RVA；字典的相對虛擬位址。  
  
    -   位元組 4-7：位移；相對於堆積開頭的位移。  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>堆積  
 堆積的大小可透過資料流讀取器來計算，計算方式是將目錄大小減去資料流長度，再加 4。 換句話說：  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 其中目錄大小為 `N * 8`。  
  
 堆積上每個具現化資訊項目的格式為：  
  
-   這個具現化資訊項目的長度 (以位元組為單位)，採用壓縮的 ECMA 中繼資料格式。 該值不包括這個長度資訊。  
  
-   泛型具現化類型數目或*T*，採用壓縮的 ECMA 中繼資料格式。  
  
-   *T*類型，分別表示以 ECMA 類型簽章格式。  
  
 包含每個堆積項目的長度可簡化目錄區段的排序，而不影響堆積。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugSymbolProvider2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
