---
title: "WMI 和效能計數器 （Unmanaged API 參考）"
description: "摘要說明.NET Framework unmanaged API 的 WMI 和效能計數器資訊。"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.date: 11/06/2017
ms.topic: article-type-from-white-list
ms.prod: .net-framework
ms.devlang: cpp
ms.openlocfilehash: 461d90aaf5beca1c0f1d1965ce0ea07411e56e79
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Management Instrumentation (WMI) 和效能計數器 （Unmanaged API 參考）

.NET Framework WMI 和效能計數器未受管理的 API 包含一組會包裝對呼叫的函式[原生 Windows Management Instrumentation API](https://msdn.microsoft.com/library/aa389276(v=vs.85).aspx)。 它可讓您開發工具和程式庫的管理和監視遠端電腦的系統。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
此 API 包含下列功能：

| 函式 | 說明 |
|---------|---------|
| [BeginEnumeration 函式](beginenumeration.md) | 將列舉值重設 WMI 物件屬性之列舉的開頭。 |
| [BeginMethodEnumeration 函式](beginmethodenumeration.md) |  開始列舉物件的可用方法的型別。 |
| [BlessIWbemServices 函式](blessiwbemservices.md) | 表示使用者認證是否允許存取指定的 IWbemServices 類別。 |
| [BlessIWbemServicesObject 函式](blessiwbemservicesobject.md) | 表示使用者認證是否允許存取指定的 IWbem 服務物件。 |
| [複製函式](clone.md) | 傳回目前物件的完整複本的新物件。 |
| [CloneEnumWbemClassObject 函式](cloneenumwbemclassobject.md) | 讓列舉值，並保留其目前位置列舉中的邏輯副本。 |
| [CompareTo 函式](compareto.md) | 比較物件與另一個 Windows 管理物件。 |
| [ConnectServerWmi 函式](connectserverwmi.md) | 指定在電腦上建立的 WMI 命名空間透過與 DCOM 的連線。 |
| [CreateClassEnumWmi 函式](createclassenumwmi.md) | 傳回符合指定的選取準則的所有類別的列舉值。 |
| [CreateInstanceEnumWmi 函式](createinstanceenumwmi.md) | 傳回列舉值，傳回符合指定的選取準則 platform 中指定的類別。 |
| [刪除函式](delete.md) | 從類別定義和所有其限定詞會刪除指定的屬性。 |
| [DeleteMethod 函式](deletemethod.md) | 從 CIM 類別定義中刪除指定的方法。 |
| [EndEnumeration 函式](endenumeration.md) | 終止列舉序列。 | 
| [EndMethodEnumeration 函式](endmethodenumeration.md) | 列舉序列結尾有啟動藉由呼叫[BeginMethodEnumeration 函式](beginmethodenumeration.md)。 |
| [ExecNotificationQueryWmi 函式](execnotificationquerywmi.md) | 執行查詢，以接收事件。 |
| [ExecQueryWmi 函式](execquerywmi.md) | 執行查詢以擷取物件。 |
| [FormatFromRawValue 函式](formatfromrawvalue.md) | 將指定的格式，一個的未經處理的效能資料值或兩個原始效能資料值的轉換，如果格式轉換是以時間為基礎。 | 
| [Get 函式](get.md) | 如果存在的話，擷取指定的屬性值。 |
| [GetCurrentApartmentType 函式](getcurrentapartmenttype.md) | 擷取的 apartment 呼叫者正在執行的所在的型別。 |
| [GetDemultiplexedStub 函式](getdemultiplexedstub.md) | 建立物件轉寄站接收可協助用戶端從 Windows 管理接收非同步呼叫。 |
| [GetErrorInfo 函式](geterrorinfo.md) | 從先前的函式呼叫中擷取資訊時發生錯誤。 | 
| [GetMethod 函式](getmethod.md) | 擷取指定之方法的相關資訊。 | 
| [GetMethodOrigin 函式](getmethodorigin.md) | 判斷在其中宣告方法的類別。 |
| [GetMethodQualifierSet 函式](getmethodqualifierset.md) | 擷取特定的方法設定的限定詞。 |
| [GetNames 函式](getnames.md) | 擷取部分或所有物件的屬性名稱。 |
| [GetObjectText 函式](getobjecttext.md) | 傳回物件的文字呈現以 MOF 語法。 | 
| [GetPropertyHandle 函式](getpropertyhandle.md) | 傳回唯一的控制代碼識別屬性。 |
| [GetPropertyOrigin 函式](getpropertyorigin.md) | 決定在宣告屬性的類別。 |
| [GetPropertyQualifierSet 函式](getpropertyqualifierset.md) | 擷取特定的屬性設定的限定詞。  |
| [GetQualifierSet 函式](getqualifierset.md) | 擷取設定的類別執行個體或類別定義的限定詞。 |
| [[Inheritsfrom] 函式](inheritsfrom.md) | 判斷目前的類別或執行個體是否衍生自指定的父類別。 |
| [Initialize 函式](initialize.md) | 執行 WMI 初始化。 |
| [下一個函式](next.md) | 擷取列舉中的下一個屬性。 | 
| [NextMethod 函式](nextmethod.md) | 擷取列舉中的下一個方法。 |
| [Put 函式](put.md) | 將具名的屬性設定為新值。 |
| [PutClassWmi 函式](putclasswmi.md) | 建立新的類別或更新現有。 |
| [PutInstanceWmi 函式](putinstancewmi.md) | 建立或更新現有類別的執行個體。 WMI 存放庫會寫入執行個體。 |
| [PutMethod 函式](putmethod.md) | 建立方法。 |
| [QualifierSet_BeginEnumeration 函式](qualifierset-beginenumeration.md) | 將物件的辨識符號的列舉值重設列舉的開頭。 |
| [QualifierSet_Delete 函式](qualifierset-delete.md) | 依名稱刪除指定的限定詞。  |
| [QualifierSet_EndEnumeration 函式](qualifierset-endenumeration.md) | 結束呼叫開始列舉`QualifierSet_BeginEnumeration`函式。 |
| [QualifierSet_Get 函式](qualifierset-get.md) | 取得指定的具名的限定詞。  |
| [QualifierSet_GetNames 函式](qualifierset-getnames.md) | 擷取所有限定詞或都是從目前的物件或屬性的指定限定詞的名稱。 |
| [QualifierSet_Next 函式](qualifierset-next.md) | 擷取列舉型別呼叫啟動下一步的限定詞[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式。 |
| [QualifierSet_Put 函式](qualifierset-put.md) | 寫入具名的辨識符號和值。 |
| [ResetSecurity 函式](resetsecurity.md) | 將提供的模擬語彙基元指派給目前的執行緒。 |
| [SetSecurity 函式](setsecurity.md) | 擷取與目前執行緒相關聯的模擬權杖。 |
| [SpawnDerivedClass 函式](spawnderivedclass.md) | 從指定的物件建立新的衍生類別物件。 | 
| [SpawnInstance 函式](spawninstance.md) | 建立類別的新執行個體。 |   
| [VerifyClient 函式](verifyclientkey.md) | 可確保用戶端金鑰具有正確的安全性。 |
| [WritePropertyValue 函式](writepropertyvalue.md) | 寫入屬性控制代碼所識別的屬性中指定的位元組數目。 |

 ## <a name="see-also"></a>請參閱
[Unmanaged 的 API 參考](../index.md) 