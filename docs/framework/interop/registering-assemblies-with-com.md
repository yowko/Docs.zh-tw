---
title: 向 COM 註冊組件
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 834652318d4cb1cbcebe27a922d210ef87026ed5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169022"
---
# <a name="registering-assemblies-with-com"></a>向 COM 註冊組件
您可以執行稱為[組件註冊工具 (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) 的命令列工具，註冊或取消登錄與 COM 搭配使用的組件。 Regasm.exe 會將此類別的相關資訊新增至容器登錄，讓 COM 用戶端可以明確地使用 .NET Framework 類別。 <xref:System.Runtime.InteropServices.RegistrationServices> 類別提供對等功能。  
  
 必須先在 Windows 登錄中註冊 Managed 元件，才能從 COM 用戶端進行啟用。 下表顯示 Regasm.exe 通常會新增至 Windows 登錄的機碼 (000000 表示實際 GUID 值)。  
  
|GUID|說明|登錄機碼|  
|----------|-----------------|------------------|  
|CLSID|類別識別碼|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|介面識別碼|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|LIBID|程式庫識別碼|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|ProgID|程式設計識別碼|HKEY_CLASSES_ROOT\000…000|  
  
 在 HKCR\CLSID\\{0000…0000} 機碼下，預設值設定為類別的 ProgID，並新增兩個新具名值：類別和組件。 執行階段會從登錄讀取 Assembly 值，並將它傳入執行階段組件解析程式。 組件解析程式會根據名稱和版本號碼這類組件資訊來嘗試找出組件。 若要讓組件解析程式找到組件，組件必須位在下列其中一個位置：  
  
-   全域組件快取 (必須是強式名稱組件)。  
  
-   在應用程式目錄中。 只有從該應用程式才能存取從應用程式路徑載入的組件。  
  
-   使用 **/codebase** 選項所指定之 Regasm.exe 的檔案路徑。  
  
 Regasm.exe 也會在 HKCR\CLSID\\{0000…0000} 機碼下建立 InProcServer32 機碼。 索引鍵的預設值設為初始化 Common Language Runtime 的 DLL 名稱 (Mscoree.dll)。  
  
## <a name="examining-registry-entries"></a>檢查登錄項目  
 COM Interop 提供標準 Class Factory 實作，來建立任何 .NET Framework 類別的執行個體。 用戶端可以在 Managed DLL 上呼叫 **DllGetClassObject**，來取得 Class Factory 以及建立物件，就像使用任何其他 COM 元件一樣。  
  
 針對 `InprocServer32` 索引鍵，Mscoree.dll 的參考會取代傳統 COM 型別程式庫，以指出 Common Language Runtime 建立 Managed 物件。  
  
## <a name="see-also"></a>另請參閱

- [將 .NET Framework 元件公開給 COM](exposing-dotnet-components-to-com.md)
- [作法：參考 COM 的 .NET 類型](how-to-reference-net-types-from-com.md)
- [呼叫 .NET 物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [部署供 COM 存取的應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
