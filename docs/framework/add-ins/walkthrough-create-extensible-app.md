---
title: 逐步解說：建立可延伸應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63780583d035d6fab6b3a79424857b82a910ef09
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155073"
---
# <a name="walkthrough-creating-an-extensible-application"></a>逐步解說：建立可延伸應用程式
本逐步解說描述如何建立增益集執行簡單的計算機功能的管線。 它不會示範真實世界的案例;相反地，它會示範管線和如何增益集可以提供服務主機的基本的功能。  
  
 此逐步解說將說明下列工作：  
  
-   建立 Visual Studio 方案。  
  
-   建立管線目錄結構。  
  
-   正在建立的合約和檢視表。  
  
-   建立增益集端配接器。  
  
-   建立主應用程式端配接器。  
  
-   建立主應用程式。  
  
-   建立增益集。  
  
-   部署管線。  
  
-   執行主應用程式。  
  
 這個管線會將傳遞的可序列化的型別 (<xref:System.Double>和<xref:System.String>)、 主機和增益集之間。 如需示範如何將複雜資料型別集合的範例，請參閱[逐步解說：主機和增益集之間傳遞集合](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)。  
  
 此管線的合約會定義四個數學運算的物件模型： 新增、 減、 乘、 和分割。 與方程式來計算，例如 2 + 2，主機會提供增益集和增益集將結果傳回至主應用程式。  
  
 計算機增益集的第 2 版提供更多計算的可能性，並示範了版本控制。 中描述[逐步解說：啟用主應用程式變更的回溯相容性](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列項目才能完成本逐步解說：  
  
-   Visual Studio。  
  
## <a name="creating-a-visual-studio-solution"></a>建立 Visual Studio 方案  
 使用 Visual Studio 中的解決方案，以包含您管線區段的專案。  
  
#### <a name="to-create-the-pipeline-solution"></a>若要建立管線的方案  
  
1.  在 Visual Studio 中建立新的專案，名為`Calc1Contract`。 它的基礎**類別庫**範本。  
  
2.  將方案命名為 `CalculatorV1`。  
  
## <a name="creating-the-pipeline-directory-structure"></a>建立管線目錄結構  
 增益集模型要求管線區段組件放在指定的目錄結構。 如需有關管線結構的詳細資訊，請參閱[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>若要建立管線目錄結構  
  
1.  在您的電腦上的任何位置建立應用程式資料夾。  
  
2.  在該資料夾中，建立下列結構：  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     不需要在您的應用程式的資料夾; 中放入管線資料夾結構此處作法僅是為了方便起見。 在適當的步驟，逐步解說會說明如何變更程式碼，如果管線資料夾結構是在不同的位置。 請參閱中的管線目錄需求的討論[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
    > [!NOTE]
    >  `CalcV2`資料夾不會用於本逐步解說，它是一個預留位置，如[逐步解說：啟用主應用程式變更的回溯相容性](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。  
  
## <a name="creating-the-contract-and-views"></a>建立合約和檢視  
 此管線的合約區段會定義`ICalc1Contract`介面，定義四種方法： `add`， `subtract`， `multiply`，和`divide`。  
  
#### <a name="to-create-the-contract"></a>若要建立合約  
  
1.  在 Visual Studio 方案中名為`CalculatorV1`，開啟`Calc1Contract`專案。  
  
2.  在 [**方案總管] 中**，將參考加入至下列組件`Calc1Contract`專案：  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  在 **方案總管**，排除新加入的預設類別**類別庫**專案。  
  
4.  在 **方案總管**，將新的項目新增至專案中，使用**介面**範本。 在 [**加入新項目**] 對話方塊中，介面名稱`ICalc1Contract`。  
  
5.  在介面檔案中加入命名空間的參考<xref:System.AddIn.Contract>和<xref:System.AddIn.Pipeline>。  
  
6.  您可以使用下列程式碼來完成此合約區段。 請注意，此介面必須<xref:System.AddIn.Pipeline.AddInContractAttribute>屬性。  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  （選擇性） 建置的 Visual Studio 方案。 方案無法執行，直到最後的程序，但每個程序可確保每個專案之後，請建置它修正。  
  
 由於增益集 檢視和主應用程式檢視的增益集通常會有相同的程式碼，尤其是在增益集的第一個版本，您可以輕鬆在同一時間建立檢視。 它們只能有一個因數的差異： 增益集檢視需要<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性，而主應用程式檢視的增益集不需要任何屬性。  
  
#### <a name="to-create-the-add-in-view"></a>若要建立增益集檢視  
  
1.  加入新的專案，名為`Calc1AddInView`至`CalculatorV1`解決方案。 它的基礎**類別庫**範本。  
  
2.  在 **方案總管**，將參考加入至 System.AddIn.dll`Calc1AddInView`專案。  
  
3.  在 [**方案總管] 中**，排除新加入的預設類別**類別庫**專案，並將新的項目新增至專案中，使用**介面**範本。 在 [**加入新項目**] 對話方塊中，介面名稱`ICalculator`。  
  
4.  在介面檔案中新增的命名空間參考<xref:System.AddIn.Pipeline>。  
  
5.  您可以使用下列程式碼來完成此增益集檢視。 請注意，此介面必須<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性。  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  （選擇性） 建置的 Visual Studio 方案。  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>若要建立的增益集的 [主機] 檢視  
  
1.  加入新的專案，名為`Calc1HVA`至`CalculatorV1`解決方案。 它的基礎**類別庫**範本。  
  
2.  在 [**方案總管] 中**，排除新加入的預設類別**類別庫**專案，並將新的項目新增至專案中，使用**介面**範本。 在 [**加入新項目**] 對話方塊中，介面名稱`ICalculator`。  
  
3.  在介面檔案中，使用下列程式碼來完成增益集的 [主機] 檢視。  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-add-in-side-adapter"></a>建立增益集端配接器  
 此增益集端配接器是由一個檢視至合約配接器所組成。 此管線區段會轉換的類型從增益集檢視的合約。  
  
 在此管線中，增益集提供服務給主機，及類型流程從增益集主應用程式。 由於沒有型別從主機到增益集，您不必包含在此管線的增益集端上的合約至檢視配接器。  
  
#### <a name="to-create-the-add-in-side-adapter"></a>若要建立增益集端配接器  
  
1.  加入新的專案，名為`Calc1AddInSideAdapter`至`CalculatorV1`解決方案。 它的基礎**類別庫**範本。  
  
2.  在 [**方案總管] 中**，將參考加入至下列組件`Calc1AddInSideAdapter`專案：  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  將專案參考加入專案相鄰的管線區段：  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  選取每個專案參考，然後在**屬性**設定**複製到本機**來**False**。 在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**為兩個專案參考。  
  
5.  重新命名專案的預設類別`CalculatorViewToContractAddInSideAdapter`。  
  
6.  在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。  
  
7.  在類別檔案中，加入相鄰的區段的命名空間參考：`CalcAddInViews`和`CalculatorContracts`。 (在 Visual Basic 中為這些命名空間參考`Calc1AddInView.CalcAddInViews`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉預設的命名空間。)  
  
8.  適用於<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性設定為`CalculatorViewToContractAddInSideAdapter`類別，將其識別為增益集端配接器。  
  
9. 製作`CalculatorViewToContractAddInSideAdapter`類別繼承<xref:System.AddIn.Pipeline.ContractBase>，以提供的預設實作<xref:System.AddIn.Contract.IContract>介面，並實作合約介面，將管線`ICalc1Contract`。  
  
10. 新增公用建構函式可接受`ICalculator`，在私用欄位中，將其快取，並呼叫基底類別建構函式。  
  
11. 若要實作的成員`ICalc1Contract`，只要呼叫的對應成員`ICalculator`會傳遞至建構函式，並傳回結果的執行個體。 這會適應檢視 (`ICalculator`) 的合約 (`ICalc1Contract`)。  
  
     下列程式碼會顯示已完成的增益集端配接器。  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-host-side-adapter"></a>建立主應用程式端配接器  
 這個主應用程式端配接器是由一個合約至檢視配接器所組成。 此區段會適應增益集的 [主機] 檢視的合約。  
  
 在此管線中，增益集提供服務主機和類型的流程從增益集主應用程式。 由於沒有型別從主機到增益集，您不必包含檢視至合約配接器。  
  
 若要實作存留期管理，請使用<xref:System.AddIn.Pipeline.ContractHandle>將存留期語彙基元新增至合約的物件。 為了讓工作的存留期管理，您必須保持此控制代碼的參考。 套用權杖之後，任何其他的程式設計需要不，因為增益集系統可處置物件時不會再使用，讓它們可供記憶體回收。 如需詳細資訊，請參閱 [生命週期管理](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)。  
  
#### <a name="to-create-the-host-side-adapter"></a>若要建立主應用程式端配接器  
  
1.  加入新的專案，名為`Calc1HostSideAdapter`至`CalculatorV1`解決方案。 它的基礎**類別庫**範本。  
  
2.  在 [**方案總管] 中**，將參考加入至下列組件`Calc1HostSideAdapter`專案：  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  將專案參考加入專案相鄰的區段：  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  選取每個專案參考，然後在**屬性**設定**複製到本機**來**False**。 在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**為兩個專案參考。  
  
5.  重新命名專案的預設類別`CalculatorContractToViewHostSideAdapter`。  
  
6.  在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。  
  
7.  在類別檔案中，加入相鄰的區段的命名空間參考：`CalcHVAs`和`CalculatorContracts`。 (在 Visual Basic 中為這些命名空間參考`Calc1HVA.CalcHVAs`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉預設的命名空間。)  
  
8.  適用於<xref:System.AddIn.Pipeline.HostAdapterAttribute>屬性設定為`CalculatorContractToViewHostSideAdapter`類別，將其識別為主應用程式端配接器區段。  
  
9. 製作`CalculatorContractToViewHostSideAdapter`類別實作介面，代表增益集的 [主機] 檢視： `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic 中)。  
  
10. 新增公用建構函式可接受管線的合約型別， `ICalc1Contract`。 建構函式必須快取之合約的參考。 它也必須建立並快取新<xref:System.AddIn.Pipeline.ContractHandle>合約，若要管理的增益集的存留期。  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle>務必存留期管理。 如果您無法將參考<xref:System.AddIn.Pipeline.ContractHandle>物件，記憶體回收會回收，而且管線時您的程式不會預期它將會關機。 這可能會導致很難進行診斷，這類的錯誤<xref:System.AppDomainUnloadedException>。 關閉是管線的正常，生命週期階段，因此沒有任何方法來偵測這種情況，會產生錯誤的存留期管理程式碼。  
  
11. 若要實作的成員`ICalculator`，只要呼叫的對應成員`ICalc1Contract`會傳遞至建構函式，並傳回結果的執行個體。 這會適應合約 (`ICalc1Contract`) 來檢視 (`ICalculator`)。  
  
     下列程式碼會顯示已完成的主應用程式端配接器。  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-host"></a>建立主應用程式  
 主應用程式互動的增益集透過增益集的 [主機] 檢視。 它會使用增益集探索和啟動方法所提供<xref:System.AddIn.Hosting.AddInStore>和<xref:System.AddIn.Hosting.AddInToken>類別來執行下列動作：  
  
-   更新快取的管線和增益集的資訊。  
  
-   尋找增益集主應用程式檢視型別， `ICalculator`，指定的管線的根目錄下。  
  
-   提示使用者指定的增益集使用。  
  
-   啟用所選增益集在新的應用程式定義域，以指定的安全性信任層級。  
  
-   執行自訂`RunCalculator`方法，它會呼叫增益集的增益集的 [主機] 檢視所指定的方法。  
  
#### <a name="to-create-the-host"></a>若要建立主應用程式  
  
1.  加入新的專案，名為`Calc1Host`至`CalculatorV1`解決方案。 它的基礎**主控台應用程式**範本。  
  
2.  在 [**方案總管] 中**，將參考加入 System.AddIn.dll 組件，以`Calc1Host`專案。  
  
3.  加入專案參考`Calc1HVA`專案。 選取該專案的參考，然後在**屬性**設定**複製到本機**來**False**。 在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**。  
  
4.  重新命名類別檔案 （在 Visual Basic 中的模組） `MathHost1`。  
  
5.  在 Visual Basic 中使用**應用程式**索引標籤**專案屬性**對話方塊，即可設定**啟始物件**至**Sub Main**。  
  
6.  在類別或模組檔案中新增的命名空間參考<xref:System.AddIn.Hosting>。  
  
7.  在類別或模組檔案中，加入 增益集的 主機 檢視的命名空間參考： `CalcHVAs`。 (在 Visual Basic 中為此命名空間參考`Calc1HVA.CalcHVAs`，除非您已在 Visual Basic 專案中關閉預設的命名空間。)  
  
8.  中**方案總管**，選取方案並從**專案**功能表中選擇 **屬性**。 在 [**方案屬性頁**] 對話方塊中，將**單一啟始專案**是這個主應用程式專案。  
  
9. 在類別或模組檔案中，使用<xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType>方法來更新快取。 使用 <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType>方法來取得語彙基元的集合，並使用<xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType>方法來啟動增益集。  
  
     下列程式碼會顯示已完成的主應用程式。  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  此程式碼會假設管線資料夾結構位於應用程式資料夾中。 如果您位於其他地方，變更設定的程式碼行`addInRoot`變數，使該變數包含您管線目錄結構的路徑。  
  
     此程式碼使用`ChooseCalculator`方法清單的權杖，並提示使用者選擇增益集。 `RunCalculator`方法提示使用者提供簡單的數學運算式，會使用運算式的剖析`Parser`類別，而且會顯示增益集所傳回的結果。  
  
10. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-add-in"></a>建立增益集  
 增益集實作增益集檢視所指定的方法。 此增益集實作`Add`， `Subtract`， `Multiply`，和`Divide`作業並將結果傳回到主應用程式。  
  
#### <a name="to-create-the-add-in"></a>若要建立增益集  
  
1.  加入新的專案，名為`AddInCalcV1`至`CalculatorV1`解決方案。 它的基礎**類別庫**範本。  
  
2.  在 [**方案總管] 中**，System.AddIn.dll 組件的參考加入專案。  
  
3.  加入專案參考`Calc1AddInView`專案。 選取該專案的參考，然後在**屬性**，將**複製到本機**來**False**。 在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**專案參考。  
  
4.  將類別重新命名`AddInCalcV1`。  
  
5.  在類別檔案中新增的命名空間參考<xref:System.AddIn>與增益集檢視區段： `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic 中)。  
  
6.  適用於<xref:System.AddIn.AddInAttribute>屬性設定為`AddInCalcV1`類別，以將類別識別為增益集。  
  
7.  製作`AddInCalcV1`類別實作代表增益集檢視的介面： `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic 中)。  
  
8.  實作的成員`ICalculator`藉由傳回適當的計算的結果。  
  
     下列程式碼顯示已完成的增益集。  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="deploying-the-pipeline"></a>部署管線  
 您現在已準備好建置及部署必要的管線目錄結構的增益集的區段。  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>將區段部署至管線  
  
1.  在方案中每個專案都使用**建置**索引標籤**專案屬性**(**編譯** 索引標籤，在 Visual Basic 中的) 設定的值**輸出路徑** (**建置輸出路徑**Visual Basic 中)。 如果您已命名為您的應用程式資料夾`MyApp`，比方說，您的專案會建置到下列資料夾：  
  
    |專案|路徑|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|MyApp|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|MyApp|  
  
    > [!NOTE]
    >  如果您決定要將您的管線資料夾結構放在您的應用程式資料夾以外的位置，您必須修改資料表中顯示的對應路徑。 請參閱中的管線目錄需求的討論[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
2.  建置 Visual Studio 方案。  
  
3.  請檢查以確保組件已複製到正確的目錄，而且沒有額外的複本，組件已安裝錯誤的資料夾中的應用程式和管線的目錄。  
  
    > [!NOTE]
    >  如果您沒有變更**複製到本機**要**False** for`Calc1AddInView`專案中的參考`AddInCalcV1`專案中，載入器內容的問題會阻礙增益集位於。  
  
     如需部署到管線的相關資訊，請參閱[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
## <a name="running-the-host-application"></a>執行主應用程式  
 您現在已準備好執行主機和增益集與互動。  
  
#### <a name="to-run-the-host-application"></a>若要執行主應用程式  
  
1.  在命令提示字元中，移至應用程式目錄並執行主應用程式， `Calc1Host.exe`。  
  
2.  主應用程式會尋找其類型的所有可用增益，並提示您選取的增益集。 請輸入**1** for 唯一可用的增益集。  
  
3.  這類計算機中，輸入一個方程式**2 + 2**。 必須有數字和運算子之間的空格。  
  
4.  型別**結束**然後按**Enter**鍵以關閉應用程式。  
  
## <a name="see-also"></a>另請參閱  
- [逐步解說：啟用主應用程式變更的回溯相容性](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
-  [逐步解說：主機和增益集之間傳遞集合](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
-  [管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
-  [合約、 檢視和配接器](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
-  [管線開發](../../../docs/framework/add-ins/pipeline-development.md)
