---
title: "互通性概觀 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7e4bc1814ed5c86660b4333542a3dc4eb7462e89
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="interoperability-overview-c-programming-guide"></a>互通性概觀 (C# 程式設計手冊)
本主題說明可在 C# Managed 程式碼和 Unmanaged 程式碼之間啟用互通性的方法。  
  
## <a name="platform-invoke"></a>平台叫用  
 「平台叫用」服務，可讓 Managed 程式碼呼叫 Unmanaged 函式在動態連結程式庫 (DLL) 中實作，例如 Win32 API 中。 它會找出並叫用匯出的函式，並且在需要的時候於交互操作界限之間封送處理其引數 (整數、 字串、 陣列、 結構和其他) 。  
  
 如需詳細資訊，請參閱[使用 Unmanaged DLL 函式](../../../framework/interop/consuming-unmanaged-dll-functions.md)和[如何：使用平台叫用播放 WAV 檔](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)。  
  
> [!NOTE]
>  [Common Language Runtime](../../../standard/clr.md) (CLR) 管理對系統資源的存取。 在 CLR 外部呼叫 Unmanaged 程式碼會略過此安全性機制，因而造成安全性風險。 例如，Unmanaged 程式碼可能會直接呼叫 Unmanaged 程式碼中的資源，並略過 CLR 安全性機制。 如需詳細資訊，請參閱 [.NET Framework 安全性](http://go.microsoft.com/fwlink/?LinkId=37122)。  
  
## <a name="c-interop"></a>C++ Interop  
 您可以使用 C++ Interop (也稱為 It Just Works (IJW)) 包裝原生 C++ 類別，以供使用 C# 或其他 .NET Framework 語言撰寫的程式碼取用。 若要這樣做，您可以撰寫 C++ 程式碼來包裝原生 DLL 或 COM 元件。 不同於其他 .NET Framework 語言，[!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] 提供互通性支援，因此可將 Managed 和 Unmanaged 程式碼放置在相同的應用程式，甚至是相同的檔案中。 您接著可使用 **/clr** 編譯器參數建立 C++ 程式碼，以產生 Managed 組件。 最後，您可以在 C# 專案中新增組件的參考，並使用包裝的物件，就像是使用其他 Managed 類別一樣。  
  
## <a name="exposing-com-components-to-c"></a>將 COM 元件公開給 C#  
 您可以從 C# 專案取用 COM 元件。 一般步驟如下所示：  
  
1.  找出並註冊所要使用的 COM 元件。 使用 regsvr32.exe 註冊或取消註冊 COM DLL。  
  
2.  將 COM 元件或型別程式庫的參考新增至專案。  
  
     當您新增參考時，[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 會使用接受型別程式庫作為輸入的 [Tlbimp.exe (型別程式庫匯入工具)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)，以輸出 .NET Framework Interop 組件。 此組件 (也稱為執行階段可呼叫包裝函式 (RCW)) 包含 Managed 類別和介面，以包裝型別程式庫中的 COM 類別和介面。 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 會將產生的組件參考新增至專案。  
  
3.  建立定義於 RCW 之類別的執行個體。 這會接著建立 COM 物件的執行個體。  
  
4.  就像是使用其他 Managed 物件一樣來使用此物件。 當記憶體回收將物件回收時，也會從記憶體釋放 COM 物件的執行個體。  
  
 如需詳細資訊，請參閱[將 COM 元件公開給 .NET Framework](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)。  
  
## <a name="exposing-c-to-com"></a>將 C# 公開給 COM  
 COM 用戶端可取用已正確公開的 C# 類型。 公開 C# 類型的基本步驟如下所示：  
  
1.  在 C# 專案中新增 Interop 屬性。  
  
     您可以藉由修改 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 專案屬性來顯示組件 COM。 如需詳細資訊，請參閱[組件資訊對話方塊](/visualstudio/ide/reference/assembly-information-dialog-box)。  
  
2.  產生 COM 型別程式庫並註冊供 COM 使用。  
  
     您可以修改 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 專案屬性，以自動為 COM Interop 註冊 C# 組件。 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 使用 [Regasm.exe (組件登錄工具)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)，並使用接受 Managed 組件作為輸入的 `/tlb` 命令列參數，以產生型別程式庫。 此型別程式庫描述組件中的 `public` 類型，並新增登錄項目，讓 COM 用戶端可以建立 Managed 類別。  
  
 如需詳細資訊，請參閱[將 .NET Framework 元件公開給 COM](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) 和[範例 COM 類別](../../../csharp/programming-guide/interop/example-com-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [Improving Interop Performance](http://go.microsoft.com/fwlink/?LinkId=99564) (提升 Interop 效能)  
 [COM Interop 簡介](http://go.microsoft.com/fwlink/?LinkId=112406)  
 [在受控碼和非受控碼之間進行封送處理](http://go.microsoft.com/fwlink/?LinkId=112398)  
 [與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)  
 [進階 COM 互通性](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)
