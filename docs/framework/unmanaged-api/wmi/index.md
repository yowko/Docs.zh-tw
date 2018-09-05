---
title: WMI 與效能計數器 (非受控 API 參考)
description: 摘要說明適用於 WMI 與效能計數器的 .NET Framework 非受控 API 資訊。
author: rpetrusha
ms.author: ronpet
ms.date: 11/06/2017
ms.openlocfilehash: 6e105bc28b6011c3177216aba996eb85c0766ac8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742773"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Management Instrumentation (WMI) 與效能計數器 (非受控 API 參考)

.NET Framework WMI 與效能計數器非受控 API 是由一組封裝對[原生 Windows Management Instrumentation API](/windows/desktop/WmiSdk/com-api-for-wmi) 之呼叫的函式所組成。 它可讓您開發可用來管理及監視遠端電腦系統的工具與程式庫。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
該 API 包括下列功能：

| 功能 | 描述 |
|---------|---------|
| [BeginEnumeration 函式](beginenumeration.md) | 將列舉程式設定為開始列舉 WMI 物件屬性的狀態。 |
| [BeginMethodEnumeration 函式](beginmethodenumeration.md) |  開始列舉物件上的可用方法。 |
| [BlessIWbemServices 函式](blessiwbemservices.md) | 指出使用者認證是否允許存取指定的 IWbemServices 類別。 |
| [BlessIWbemServicesObject 函式](blessiwbemservicesobject.md) | 指出使用者認證是否允許存取指定的 IWbem 服務物件。 |
| [Clone 函式](clone.md) | 傳回屬於目前物件之完整複製品的新物件。 |
| [CloneEnumWbemClassObject 函式](cloneenumwbemclassobject.md) | 建立列舉程式的邏輯複本，並保留其在列舉中的目前位置。 |
| [CompareTo 函式](compareto.md) | 將物件與另一個 Windows 管理物件比較。 |
| [ConnectServerWmi 函式](connectserverwmi.md) | 在指定的電腦上建立從 DCOM 到 WMI 命名空間的連線。 |
| [CreateClassEnumWmi 函式](createclassenumwmi.md) | 傳回滿足所指定選取條件之所有類別的列舉程式。 |
| [CreateInstanceEnumWmi 函式](createinstanceenumwmi.md) | 傳回會傳回滿足指定選取條件之指定類別執行個體的列舉程式。 |
| [Delete 函式](delete.md) | 從類別定義與其所有限定詞刪除指定的屬性。 |
| [DeleteMethod 函式](deletemethod.md) | 從 CIM 類別定義刪除指定的方法。 |
| [EndEnumeration 函式](endenumeration.md) | 終止列舉序列。 | 
| [EndMethodEnumeration 函式](endmethodenumeration.md) | 終止透過呼叫 [BeginMethodEnumeration 函式](beginmethodenumeration.md)而開始的列舉序列。 |
| [ExecNotificationQueryWmi 函式](execnotificationquerywmi.md) | 執行查詢以接收事件。 |
| [ExecQueryWmi 函式](execquerywmi.md) | 執行查詢以擷取物件。 |
| [FormatFromRawValue 函式](formatfromrawvalue.md) | 將一個原始效能資料值轉換為指定的格式，或轉換為兩個原始效能資料值 (若格式轉換是以時間為基礎)。 | 
| [Get 函式](get.md) | 擷取指定的屬性值 (若它存在的話)。 |
| [GetCurrentApartmentType 函式](getcurrentapartmenttype.md) | 擷取呼叫者在其中執行之 Apartment 的型別。 |
| [GetDemultiplexedStub 函式](getdemultiplexedstub.md) | 建立物件轉寄站接收以協助用戶端從 Windows Management 接收非同步呼叫。 |
| [GetErrorInfo 函式](geterrorinfo.md) | 從上一個函式呼叫擷取錯誤資訊。 | 
| [GetMethod 函式](getmethod.md) | 擷取指定之方法的相關資訊。 | 
| [GetMethodOrigin 函式](getmethodorigin.md) | 判斷方法在其中宣告的類別。 |
| [GetMethodQualifierSet 函式](getmethodqualifierset.md) | 擷取特定方法的限定詞集合。 |
| [GetNames 函式](getnames.md) | 擷取物件屬性的子集合或所有名稱。 |
| [GetObjectText 函式](getobjecttext.md) | 以 MOF 語法傳回物件的文字型轉譯。 | 
| [GetPropertyHandle 函式](getpropertyhandle.md) | 傳回識別屬性的唯一控制代碼。 |
| [GetPropertyOrigin 函式](getpropertyorigin.md) | 判斷屬性在其中宣告的類別。 |
| [GetPropertyQualifierSet 函式](getpropertyqualifierset.md) | 擷取特定屬性的限定詞集合。  |
| [GetQualifierSet 函式](getqualifierset.md) | 擷取類別執行個體或類別定義的限定詞集合。 |
| [InheritsFrom 函式](inheritsfrom.md) | 判斷目前類別或執行個體衍生自指定的父類別。 |
| [Initialize 函式](initialize.md) | 執行 WMI 初始化。 |
| [Next 函式](next.md) | 擷取列舉中的下一個屬性。 | 
| [NextMethod 函式](nextmethod.md) | 擷取列舉中的下一個方法。 |
| [Put 函式](put.md) | 將具名屬性設定為新值。 |
| [PutClassWmi 函式](putclasswmi.md) | 建立新類別或更新現有類別。 |
| [PutInstanceWmi 函式](putinstancewmi.md) | 建立或更新現有類別的執行個體。 執行個體是寫入到 WMI 存放庫。 |
| [PutMethod 函式](putmethod.md) | 建立方法。 |
| [QualifierSet_BeginEnumeration 函式](qualifierset-beginenumeration.md) | 將物件限定詞的列舉程式重設為列舉開始時的狀態。 |
| [QualifierSet_Delete 函式](qualifierset-delete.md) | 依名稱刪除指定的限定詞。  |
| [QualifierSet_EndEnumeration 函式](qualifierset-endenumeration.md) | 終止透過呼叫 `QualifierSet_BeginEnumeration` 函式而開始的列舉。 |
| [QualifierSet_Get 函式](qualifierset-get.md) | 取得指定的具名限定詞。  |
| [QualifierSet_GetNames 函式](qualifierset-getnames.md) | 擷取可從目前物件或屬性取得之所有限定詞或指定限定詞的名稱。 |
| [QualifierSet_Next 函式](qualifierset-next.md) | 擷取透過呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 函式而開始之列舉中的下一個限定詞。 |
| [QualifierSet_Put 函式](qualifierset-put.md) | 寫入具名限定詞與值。 |
| [ResetSecurity 函式](resetsecurity.md) | 將提供的模擬權杖指派給目前的執行緒。 |
| [SetSecurity 函式](setsecurity.md) | 擷取與目前執行緒關聯的模擬權杖。 |
| [SpawnDerivedClass 函式](spawnderivedclass.md) | 從指定的物件建立新的衍生類別物件。 | 
| [SpawnInstance 函式](spawninstance.md) | 建立類別的新執行個體。 |   
| [VerifyClient 函式](verifyclientkey.md) | 確定用戶端金鑰有正確的安全性。 |
| [WritePropertyValue 函式](writepropertyvalue.md) | 將指定的位元組數目寫入到屬性控制代碼所指定的屬性中。 |

 ## <a name="see-also"></a>另請參閱
[非受控 API 參考](../index.md) 
