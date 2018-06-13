---
title: 如何：對應 HRESULT 和例外狀況
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d9825deae22e856cf520e6173d53278539c576c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393545"
---
# <a name="how-to-map-hresults-and-exceptions"></a>如何：對應 HRESULT 和例外狀況
COM 方法是藉由傳回 HRESULT 來報告錯誤；.NET 方法則是藉由擲回例外狀況來報告錯誤。 執行階段則負責處理兩者之間的轉換。 .NET Framework 的每一個例外狀況類別都會對應到一個 HRESULT。  
  
 使用者定義的例外狀況類別可以指定任何適當的 HRESULT。 當例外狀況是藉由設定例外狀況物件上的 **HResult** 欄位而產生時，這些例外狀況類別可以動態地變更要傳回的 HRESULT。 例外狀況的其他資訊會透過 **IErrorInfo** 介面提供給用戶端，而該介面是實作於 Unmanaged 處理序中的 .NET 物件上。  
  
 如果您建立了擴充 **System.Exception** 的類別，則必須在建構期間設定 HRESULT 欄位。 否則，基底類別會指派 HRESULT 值。 您可以在例外狀況的建構函式中提供值，將新的例外狀況類別對應到現有的 HRESULT。  
  
 請注意，執行階段有時候會忽略 `HRESULT`，以應付萬一執行緒上存在 `IErrorInfo` 的情況。  如果 `HRESULT` 和 `IErrorInfo` 並不代表相同的錯誤，就可能會發生這種行為。  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>建立新的例外狀況類別並將其對應到 HRESULT  
  
1.  使用下列程式碼來建立稱為 `NoAccessException` 的新例外狀況類別，並將其對應到 HRESULT `E_ACCESSDENIED`。  
  
    ```cpp  
    Class NoAccessException : public ApplicationException  
    {  
        NoAccessException () {  
        HResult = E_ACCESSDENIED;   
    }  
    }  
    CMyClass::MethodThatThrows  
    {  
    throw new NoAccessException();  
    }  
    ```  
  
 您也許會遇到同時使用 Managed 和 Unmanaged 程式碼的程式 (以任何程式語言所撰寫)。 例如，下列程式碼範例中的自訂封送處理器是使用 **Marshal.ThrowExceptionForHR(int HResult)** 方法來擲回具有特定 HRESULT 值的例外狀況。 此方法會查詢 HRESULT 並產生適當的例外狀況,類型。 例如，下列程式碼片段中的 HRESULT 會產生 **ArgumentException**。  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 下表提供每一個 HRESULT 與其在 .NET Framework 中可比較之例外狀況類別的完整對應。  
  
|HRESULT|.NET 例外狀況|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT 或 E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC 或 ERROR_ARITHMETIC_OVERFLOW**|**ArithmeticException**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT 或 ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**CryptographicException**|  
|**COR_E_DIRECTORYNOTFOUND 或 ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR_E_EXCEPTION**|**例外狀況**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND 或 ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST 或 E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR_E_INVALIDOLEVariantTYPE**|**InvalidOleVariantTypeException**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**IOException**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E_NOTIMPL**|**NotImplementedException**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE 或 E_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY 或**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG 或 ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
|**COR_E_RANK**|**RankException**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**RemotingException**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR_E_SECURITY**|**SecurityException**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW 或 ERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**SynchronizationLockException**|  
|**COR_E_SYSTEM**|**SystemException**|  
|**COR_E_TARGET**|**TargetException**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR_E_THREADSTATE**|**ThreadStateException**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**所有其他的 HRESULT**|**COMException**|  
  
 若要擷取擴充錯誤資訊，Managed 用戶端必須檢查所產生之例外狀況物件的欄位。 若要讓例外狀況物件提供有關錯誤的有用資訊，COM 物件必須實作 **IErrorInfo** 介面。 執行階段會使用 **IErrorInfo** 提供的資訊來初始化例外狀況物件。  
  
 如果 COM 物件不支援 **IErrorInfo**，執行階段會使用預設值來初始化例外狀況物件。 下表列出與例外狀況物件建立關聯的每一個欄位，並且指出當 COM 物件支援 **IErrorInfo** 時的預設資訊來源。  
  
 請注意，執行階段有時候會忽略 `HRESULT`，以應付萬一執行緒上存在 `IErrorInfo` 的情況。  如果 `HRESULT` 和 `IErrorInfo` 並不代表相同的錯誤，就可能會發生這種行為。  
  
|例外狀況欄位|來自 COM 的資訊來源|  
|---------------------|------------------------------------|  
|**ErrorCode**|從呼叫傳回的 HRESULT。|  
|**HelpLink**|如果 **IErrorInfo->HelpContext** 是非零值，則字串是由串連 **IErrorInfo->GetHelpFile**、"#" 和 **IErrorInfo->GetHelpContext** 所構成。 否則，字串是從 **IErrorInfo->GetHelpFile** 所傳回。|  
|**InnerException**|一律為 Null 參考 (在 Visual Basic 中為 **Nothing**)。|  
|**訊息**|從 **IErrorInfo->GetDescription** 傳回的字串。|  
|**來源**|從 **IErrorInfo->GetSource** 傳回的字串。|  
|**StackTrace**|堆疊追蹤。|  
|**TargetSite**|傳回失敗 HRESULT 之方法的名稱。|  
  
 如 **Message**、**Source** 和 **StackTrace** 之類的例外狀況欄位，並不適用於 **StackOverflowException**。  
  
## <a name="see-also"></a>請參閱  
 [進階 COM 互通性](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb(v=vs.100))  
 [例外狀況](../../standard/exceptions/index.md)
