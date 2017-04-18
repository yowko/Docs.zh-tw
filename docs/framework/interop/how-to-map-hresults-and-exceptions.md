---
title: "如何：對應 HRESULT 和例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM Interop, 例外狀況"
  - "COM Interop, HRESULT"
  - "例外狀況, HRESULT"
  - "HRESULT"
  - "與 Unmanaged 程式碼的互通, 例外狀況"
  - "與 Unmanaged 程式碼的互通, HRESULT"
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：對應 HRESULT 和例外狀況
COM 方法是藉由傳回 HRESULT 來報告錯誤；.NET 方法則是藉由擲回例外狀況來報告錯誤。  Runtime 則負責處理兩者之間的轉換。  .NET Framework 的每一個例外狀況類別都會對應到一個 HRESULT。  
  
 使用者定義的例外狀況類別可以指定任何適當的 HRESULT。  當例外狀況是藉由設定例外狀況物件上的 **HResult** 欄位而產生時，這些例外狀況類別可以動態地變更要傳回的 HRESULT。  有關例外狀況的其他資訊，會透過實作於 Unmanaged 處理序中 .NET 物件上的 **IErrorInfo** 介面提供給用戶端。  
  
 如果您建立擴充 **System.Exception** 的類別，您必須在建構期間設定 HRESULT 欄位。  否則，基底類別會指派 HRESULT 值。  您可以在例外狀況的建構函式 \(Constructor\) 中提供值，將新的例外狀況類別對應到現有的 HRESULT。  
  
 請注意，執行階段有時候會忽略 `HRESULT`，以應付萬一執行緒上存在 `IErrorInfo` 的情況。  萬一 `HRESULT` 和 `IErrorInfo` 並不表示相同的錯誤，就可能會發生這個行為。   ``  
  
### 若要建立新 Exception 類別並對應至 HRESULT  
  
1.  使用下列程式碼建立名稱為 `NoAccessException` 的新 Exception 類別，並對應至 HRESULT `E_ACCESSDENIED`。  
  
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
  
 您或許會碰到同時使用 Managed 和 Unmanaged 程式碼的程式 \(以任何程式語言所撰寫\)。  例如，下列程式碼範例中的自訂封送處理器是使用 **Marshal.ThrowExceptionForHR\(int HResult\)** 方法來擲回具有特定 HRESULT 值的例外狀況。  這個方法會查詢 HRESULT 並且產生適當的例外狀況型別。  例如，下列程式碼片段中的 HRESULT 會產生 **ArgumentException**。  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 以下表格提供從每一個 HRESULT 到它在 .NET Framework 中相當的例外狀況類別的完整對應。  
  
|HRESULT|.NET 例外狀況|  
|-------------|---------------|  
|**MSEE\_E\_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR\_E\_APPLICATION**|**ApplicationException**|  
|**COR\_E\_ARGUMENT 或 E\_INVALIDARG**|**ArgumentException**|  
|**COR\_E\_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR\_E\_ARITHMETIC 或 ERROR\_ARITHMETIC\_OVERFLOW**|**ArithmeticException**|  
|**COR\_E\_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR\_E\_BADIMAGEFORMAT 或 ERROR\_BAD\_FORMAT**|**BadImageFormatException**|  
|**COR\_E\_COMEMULATE\_ERROR**|**COMEmulateException**|  
|**COR\_E\_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR\_E\_CORE**|**CoreException**|  
|**NTE\_FAIL**|**CryptographicException**|  
|**COR\_E\_DIRECTORYNOTFOUND 或 ERROR\_PATH\_NOT\_FOUND**|**DirectoryNotFoundException**|  
|**COR\_E\_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR\_E\_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR\_E\_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR\_E\_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR\_E\_EXCEPTION**|**例外狀況**|  
|**COR\_E\_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR\_E\_FIELDACCESS**|**FieldAccessException**|  
|**COR\_E\_FILENOTFOUND 或 ERROR\_FILE\_NOT\_FOUND**|**FileNotFoundException**|  
|**COR\_E\_FORMAT**|**FormatException**|  
|**COR\_E\_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR\_E\_INVALIDCAST 或 E\_NOINTERFACE**|**InvalidCastException**|  
|**COR\_E\_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR\_E\_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR\_E\_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR\_E\_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR\_E\_IO**|**IOException**|  
|**COR\_E\_MEMBERACCESS**|**AccessException**|  
|**COR\_E\_METHODACCESS**|**MethodAccessException**|  
|**COR\_E\_MISSINGFIELD**|**MissingFieldException**|  
|**COR\_E\_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR\_E\_MISSINGMEMBER**|**MissingMemberException**|  
|**COR\_E\_MISSINGMETHOD**|**MissingMethodException**|  
|**COR\_E\_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR\_E\_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E\_NOTIMPL**|**NotImplementedException**|  
|**COR\_E\_NOTSUPPORTED**|**NotSupportedException**|  
|**COR\_E\_NULLREFERENCE 或 E\_POINTER**|**NullReferenceException**|  
|**COR\_E\_OUTOFMEMORY 或**<br /><br /> **E\_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR\_E\_OVERFLOW**|**OverflowException**|  
|**COR\_E\_PATHTOOLONG 或 ERROR\_FILENAME\_EXCED\_RANGE**|**PathTooLongException**|  
|**COR\_E\_RANK**|**RankException**|  
|**COR\_E\_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR\_E\_REMOTING**|**RemotingException**|  
|**COR\_E\_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR\_E\_SECURITY**|**SecurityException**|  
|**COR\_E\_SERIALIZATION**|**SerializationException**|  
|**COR\_E\_STACKOVERFLOW 或 ERROR\_STACK\_OVERFLOW**|**StackOverflowException**|  
|**COR\_E\_SYNCHRONIZATIONLOCK**|**SynchronizationLockException**|  
|**COR\_E\_SYSTEM**|**SystemException**|  
|**COR\_E\_TARGET**|**TargetException**|  
|**COR\_E\_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR\_E\_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR\_E\_THREADABORTED**|**ThreadAbortException**|  
|**COR\_E\_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR\_E\_THREADSTATE**|**ThreadStateException**|  
|**COR\_E\_THREADSTOP**|**ThreadStopException**|  
|**COR\_E\_TYPELOAD**|**TypeLoadException**|  
|**COR\_E\_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR\_E\_VERIFICATION**|**VerificationException**|  
|**COR\_E\_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR\_E\_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**所有其他 HRESULT**|**COMException**|  
  
 若要擷取擴充錯誤資訊，Managed 用戶端必須檢查所產生之例外狀況物件的欄位。  若要讓例外狀況物件提供有關錯誤的有用資訊，COM 物件必須實作 **IErrorInfo** 介面。  Runtime 會使用 **IErrorInfo** 提供的資訊來初始化例外狀況物件。  
  
 如果 COM 物件不支援 **IErrorInfo**，Runtime 會使用預設值來初始化例外狀況物件。  以下表格列出與例外狀況物件關聯的每一個欄位，並且指出當 COM 物件支援 **IErrorInfo** 時的預設資訊來源。  
  
 請注意，執行階段有時候會忽略 `HRESULT`，以應付萬一執行緒上存在 `IErrorInfo` 的情況。  萬一 `HRESULT` 和 `IErrorInfo` 並不表示相同的錯誤，就可能會發生這個行為。   ``  
  
|例外狀況欄位|來自 COM 的資訊來源|  
|------------|------------------|  
|**ErrorCode**|從呼叫傳回的 HRESULT。|  
|**HelpLink**|如果 **IErrorInfo\-\>HelpContext** 為非零值 \(Nonzero\)，則字串是由連結 **IErrorInfo\-\>GetHelpFile**、「\#」和 **IErrorInfo\-\>GetHelpContext** 所構成。  否則，字串是由 **IErrorInfo\-\>GetHelpFile** 所傳回。|  
|**InnerException**|一定是 Null 參考 \(在 Visual Basic 中為 **Nothing**\)。|  
|**訊息**|從 **IErrorInfo\-\>GetDescription** 傳回的字串。|  
|**來源**|從 **IErrorInfo\-\>GetSource** 傳回的字串。|  
|**StackTrace**|堆疊追蹤。|  
|**TargetSite**|傳回失敗 HRESULT 之方法的名稱。|  
  
 像 **Message**、**Source** 和 **StackTrace** 這些例外狀況欄位，並不適用於 **StackOverflowException**。  
  
## 請參閱  
 [Advanced COM Interoperability](http://msdn.microsoft.com/zh-tw/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [例外狀況](../../../docs/standard/exceptions/index.md)