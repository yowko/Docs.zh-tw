---
title: "ODBC 結構描述集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="f9ef4-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="f9ef4-102">ODBC Schema Collections</span></span>
<span data-ttu-id="f9ef4-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="f9ef4-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="f9ef4-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="f9ef4-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="f9ef4-105">Microsoft SQL Server ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="f9ef4-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f9ef4-106">資料表</span><span class="sxs-lookup"><span data-stu-id="f9ef4-106">Tables</span></span>  
  
-   <span data-ttu-id="f9ef4-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="f9ef4-107">Indexes</span></span>  
  
-   <span data-ttu-id="f9ef4-108">資料行</span><span class="sxs-lookup"><span data-stu-id="f9ef4-108">Columns</span></span>  
  
-   <span data-ttu-id="f9ef4-109">程序</span><span class="sxs-lookup"><span data-stu-id="f9ef4-109">Procedures</span></span>  
  
-   <span data-ttu-id="f9ef4-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f9ef4-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f9ef4-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f9ef4-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f9ef4-112">檢視</span><span class="sxs-lookup"><span data-stu-id="f9ef4-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f9ef4-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="f9ef4-113">Tables and Views</span></span>  
  
|<span data-ttu-id="f9ef4-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-114">ColumnName</span></span>|<span data-ttu-id="f9ef4-115">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f9ef4-116">TABLE_CAT</span></span>|<span data-ttu-id="f9ef4-117">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-117">String</span></span>|  
|<span data-ttu-id="f9ef4-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f9ef4-118">TABLE_SCHEM</span></span>|<span data-ttu-id="f9ef4-119">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-119">String</span></span>|  
|<span data-ttu-id="f9ef4-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-120">TABLE_NAME</span></span>|<span data-ttu-id="f9ef4-121">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-121">String</span></span>|  
|<span data-ttu-id="f9ef4-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-122">TABLE_TYPE</span></span>|<span data-ttu-id="f9ef4-123">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-123">String</span></span>|  
|<span data-ttu-id="f9ef4-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-124">REMARKS</span></span>|<span data-ttu-id="f9ef4-125">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f9ef4-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="f9ef4-126">Indexes</span></span>  
  
|<span data-ttu-id="f9ef4-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-127">ColumnName</span></span>|<span data-ttu-id="f9ef4-128">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f9ef4-129">TABLE_CAT</span></span>|<span data-ttu-id="f9ef4-130">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-130">String</span></span>|  
|<span data-ttu-id="f9ef4-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f9ef4-131">TABLE_SCHEM</span></span>|<span data-ttu-id="f9ef4-132">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-132">String</span></span>|  
|<span data-ttu-id="f9ef4-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-133">TABLE_NAME</span></span>|<span data-ttu-id="f9ef4-134">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-134">String</span></span>|  
|<span data-ttu-id="f9ef4-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-135">NON_UNIQUE</span></span>|<span data-ttu-id="f9ef4-136">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-136">Int16</span></span>|  
|<span data-ttu-id="f9ef4-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-138">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-138">String</span></span>|  
|<span data-ttu-id="f9ef4-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-139">INDEX_NAME</span></span>|<span data-ttu-id="f9ef4-140">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-140">String</span></span>|  
|<span data-ttu-id="f9ef4-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-141">TYPE</span></span>|<span data-ttu-id="f9ef4-142">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-142">Int16</span></span>|  
|<span data-ttu-id="f9ef4-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-144">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-144">Int16</span></span>|  
|<span data-ttu-id="f9ef4-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-145">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-146">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-146">String</span></span>|  
|<span data-ttu-id="f9ef4-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="f9ef4-147">ASC_OR_DESC</span></span>|<span data-ttu-id="f9ef4-148">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-148">String</span></span>|  
|<span data-ttu-id="f9ef4-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="f9ef4-149">CARDINATLITY</span></span>|<span data-ttu-id="f9ef4-150">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-150">Int32</span></span>|  
|<span data-ttu-id="f9ef4-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="f9ef4-151">PAGES</span></span>|<span data-ttu-id="f9ef4-152">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-152">Int32</span></span>|  
|<span data-ttu-id="f9ef4-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-153">FILTER_CONDITION</span></span>|<span data-ttu-id="f9ef4-154">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-154">String</span></span>|  
|<span data-ttu-id="f9ef4-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f9ef4-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f9ef4-156">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-156">String</span></span>|  
|<span data-ttu-id="f9ef4-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-158">Byte</span><span class="sxs-lookup"><span data-stu-id="f9ef4-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f9ef4-159">資料行</span><span class="sxs-lookup"><span data-stu-id="f9ef4-159">Columns</span></span>  
  
|<span data-ttu-id="f9ef4-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-160">ColumnName</span></span>|<span data-ttu-id="f9ef4-161">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f9ef4-162">TABLE_CAT</span></span>|<span data-ttu-id="f9ef4-163">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-163">String</span></span>|  
|<span data-ttu-id="f9ef4-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f9ef4-164">TABLE_SCHEM</span></span>|<span data-ttu-id="f9ef4-165">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-165">String</span></span>|  
|<span data-ttu-id="f9ef4-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-166">TABLE_NAME</span></span>|<span data-ttu-id="f9ef4-167">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-167">String</span></span>|  
|<span data-ttu-id="f9ef4-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-168">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-169">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-169">String</span></span>|  
|<span data-ttu-id="f9ef4-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-170">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-171">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-171">Int16</span></span>|  
|<span data-ttu-id="f9ef4-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-172">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-173">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-173">String</span></span>|  
|<span data-ttu-id="f9ef4-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-174">COLUMN_SIZE</span></span>|<span data-ttu-id="f9ef4-175">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-175">Int32</span></span>|  
|<span data-ttu-id="f9ef4-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="f9ef4-177">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-177">Int32</span></span>|  
|<span data-ttu-id="f9ef4-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f9ef4-179">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-179">Int16</span></span>|  
|<span data-ttu-id="f9ef4-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f9ef4-181">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-181">Int16</span></span>|  
|<span data-ttu-id="f9ef4-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-182">NULLABLE</span></span>|<span data-ttu-id="f9ef4-183">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-183">Int16</span></span>|  
|<span data-ttu-id="f9ef4-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-184">REMARKS</span></span>|<span data-ttu-id="f9ef4-185">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-185">String</span></span>|  
|<span data-ttu-id="f9ef4-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f9ef4-186">COLUMN_DEF</span></span>|<span data-ttu-id="f9ef4-187">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-187">String</span></span>|  
|<span data-ttu-id="f9ef4-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-189">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-189">Int16</span></span>|  
|<span data-ttu-id="f9ef4-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f9ef4-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f9ef4-191">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-191">Int16</span></span>|  
|<span data-ttu-id="f9ef4-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f9ef4-193">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-193">Int32</span></span>|  
|<span data-ttu-id="f9ef4-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-195">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-195">Int32</span></span>|  
|<span data-ttu-id="f9ef4-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-196">IS_NULLABLE</span></span>|<span data-ttu-id="f9ef4-197">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-197">String</span></span>|  
|<span data-ttu-id="f9ef4-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f9ef4-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f9ef4-199">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-199">String</span></span>|  
|<span data-ttu-id="f9ef4-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f9ef4-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f9ef4-201">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-201">String</span></span>|  
|<span data-ttu-id="f9ef4-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-203">Byte</span><span class="sxs-lookup"><span data-stu-id="f9ef4-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f9ef4-204">程序</span><span class="sxs-lookup"><span data-stu-id="f9ef4-204">Procedures</span></span>  
  
|<span data-ttu-id="f9ef4-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-205">ColumnName</span></span>|<span data-ttu-id="f9ef4-206">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f9ef4-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="f9ef4-208">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-208">String</span></span>|  
|<span data-ttu-id="f9ef4-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f9ef4-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f9ef4-210">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-210">String</span></span>|  
|<span data-ttu-id="f9ef4-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-212">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-212">String</span></span>|  
|<span data-ttu-id="f9ef4-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f9ef4-214">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-214">Int32</span></span>|  
|<span data-ttu-id="f9ef4-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f9ef4-216">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-216">Int32</span></span>|  
|<span data-ttu-id="f9ef4-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f9ef4-218">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-218">Int32</span></span>|  
|<span data-ttu-id="f9ef4-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-219">REMARKS</span></span>|<span data-ttu-id="f9ef4-220">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-220">String</span></span>|  
|<span data-ttu-id="f9ef4-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f9ef4-222">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f9ef4-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f9ef4-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f9ef4-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-224">ColumnName</span></span>|<span data-ttu-id="f9ef4-225">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f9ef4-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="f9ef4-227">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-227">String</span></span>|  
|<span data-ttu-id="f9ef4-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f9ef4-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f9ef4-229">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-229">String</span></span>|  
|<span data-ttu-id="f9ef4-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-231">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-231">String</span></span>|  
|<span data-ttu-id="f9ef4-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-232">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-233">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-233">String</span></span>|  
|<span data-ttu-id="f9ef4-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-234">COLUMN_TYPE</span></span>|<span data-ttu-id="f9ef4-235">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-235">Int16</span></span>|  
|<span data-ttu-id="f9ef4-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-236">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-237">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-237">Int16</span></span>|  
|<span data-ttu-id="f9ef4-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-238">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-239">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-239">String</span></span>|  
|<span data-ttu-id="f9ef4-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-240">COLUMN_SIZE</span></span>|<span data-ttu-id="f9ef4-241">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-241">Int32</span></span>|  
|<span data-ttu-id="f9ef4-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="f9ef4-243">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-243">Int32</span></span>|  
|<span data-ttu-id="f9ef4-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f9ef4-245">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-245">Int16</span></span>|  
|<span data-ttu-id="f9ef4-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f9ef4-247">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-247">Int16</span></span>|  
|<span data-ttu-id="f9ef4-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-248">NULLABLE</span></span>|<span data-ttu-id="f9ef4-249">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-249">Int16</span></span>|  
|<span data-ttu-id="f9ef4-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-250">REMARKS</span></span>|<span data-ttu-id="f9ef4-251">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-251">String</span></span>|  
|<span data-ttu-id="f9ef4-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f9ef4-252">COLUMN_DEF</span></span>|<span data-ttu-id="f9ef4-253">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-253">String</span></span>|  
|<span data-ttu-id="f9ef4-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-255">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-255">Int16</span></span>|  
|<span data-ttu-id="f9ef4-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f9ef4-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f9ef4-257">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-257">Int16</span></span>|  
|<span data-ttu-id="f9ef4-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f9ef4-259">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-259">Int32</span></span>|  
|<span data-ttu-id="f9ef4-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-261">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-261">Int32</span></span>|  
|<span data-ttu-id="f9ef4-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-262">IS_NULLABLE</span></span>|<span data-ttu-id="f9ef4-263">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-263">String</span></span>|  
|<span data-ttu-id="f9ef4-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f9ef4-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f9ef4-265">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-265">String</span></span>|  
|<span data-ttu-id="f9ef4-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f9ef4-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f9ef4-267">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-267">String</span></span>|  
|<span data-ttu-id="f9ef4-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-269">Byte</span><span class="sxs-lookup"><span data-stu-id="f9ef4-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f9ef4-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f9ef4-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f9ef4-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-271">ColumnName</span></span>|<span data-ttu-id="f9ef4-272">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f9ef4-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="f9ef4-274">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-274">String</span></span>|  
|<span data-ttu-id="f9ef4-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f9ef4-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f9ef4-276">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-276">String</span></span>|  
|<span data-ttu-id="f9ef4-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-278">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-278">String</span></span>|  
|<span data-ttu-id="f9ef4-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-279">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-280">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-280">String</span></span>|  
|<span data-ttu-id="f9ef4-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-281">COLUMN_TYPE</span></span>|<span data-ttu-id="f9ef4-282">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-282">Int16</span></span>|  
|<span data-ttu-id="f9ef4-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-283">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-284">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-284">Int16</span></span>|  
|<span data-ttu-id="f9ef4-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-285">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-286">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-286">String</span></span>|  
|<span data-ttu-id="f9ef4-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-287">COLUMN_SIZE</span></span>|<span data-ttu-id="f9ef4-288">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-288">Int32</span></span>|  
|<span data-ttu-id="f9ef4-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="f9ef4-290">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-290">Int32</span></span>|  
|<span data-ttu-id="f9ef4-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f9ef4-292">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-292">Int16</span></span>|  
|<span data-ttu-id="f9ef4-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f9ef4-294">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-294">Int16</span></span>|  
|<span data-ttu-id="f9ef4-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-295">NULLABLE</span></span>|<span data-ttu-id="f9ef4-296">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-296">Int16</span></span>|  
|<span data-ttu-id="f9ef4-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-297">REMARKS</span></span>|<span data-ttu-id="f9ef4-298">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-298">String</span></span>|  
|<span data-ttu-id="f9ef4-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f9ef4-299">COLUMN_DEF</span></span>|<span data-ttu-id="f9ef4-300">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-300">String</span></span>|  
|<span data-ttu-id="f9ef4-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-302">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-302">Int16</span></span>|  
|<span data-ttu-id="f9ef4-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f9ef4-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f9ef4-304">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-304">Int16</span></span>|  
|<span data-ttu-id="f9ef4-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f9ef4-306">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-306">Int32</span></span>|  
|<span data-ttu-id="f9ef4-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-308">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-308">Int32</span></span>|  
|<span data-ttu-id="f9ef4-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-309">IS_NULLABLE</span></span>|<span data-ttu-id="f9ef4-310">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-310">String</span></span>|  
|<span data-ttu-id="f9ef4-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f9ef4-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f9ef4-312">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-312">String</span></span>|  
|<span data-ttu-id="f9ef4-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f9ef4-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f9ef4-314">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-314">String</span></span>|  
|<span data-ttu-id="f9ef4-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-316">Byte</span><span class="sxs-lookup"><span data-stu-id="f9ef4-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="f9ef4-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="f9ef4-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="f9ef4-318">Microsoft SQL Server Oracle ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="f9ef4-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f9ef4-319">資料表</span><span class="sxs-lookup"><span data-stu-id="f9ef4-319">Tables</span></span>  
  
-   <span data-ttu-id="f9ef4-320">資料行</span><span class="sxs-lookup"><span data-stu-id="f9ef4-320">Columns</span></span>  
  
-   <span data-ttu-id="f9ef4-321">程序</span><span class="sxs-lookup"><span data-stu-id="f9ef4-321">Procedures</span></span>  
  
-   <span data-ttu-id="f9ef4-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f9ef4-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f9ef4-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f9ef4-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f9ef4-324">檢視</span><span class="sxs-lookup"><span data-stu-id="f9ef4-324">Views</span></span>  
  
-   <span data-ttu-id="f9ef4-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="f9ef4-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f9ef4-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="f9ef4-326">Tables and Views</span></span>  
  
|<span data-ttu-id="f9ef4-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-327">ColumnName</span></span>|<span data-ttu-id="f9ef4-328">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-330">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-330">String</span></span>|  
|<span data-ttu-id="f9ef4-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-331">TABLE_OWNER</span></span>|<span data-ttu-id="f9ef4-332">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-332">String</span></span>|  
|<span data-ttu-id="f9ef4-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-333">TABLE_NAME</span></span>|<span data-ttu-id="f9ef4-334">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-334">String</span></span>|  
|<span data-ttu-id="f9ef4-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-335">TABLE_TYPE</span></span>|<span data-ttu-id="f9ef4-336">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-336">String</span></span>|  
|<span data-ttu-id="f9ef4-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-337">REMARKS</span></span>|<span data-ttu-id="f9ef4-338">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f9ef4-339">資料行</span><span class="sxs-lookup"><span data-stu-id="f9ef4-339">Columns</span></span>  
  
|<span data-ttu-id="f9ef4-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-340">ColumnName</span></span>|<span data-ttu-id="f9ef4-341">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-343">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-343">String</span></span>|  
|<span data-ttu-id="f9ef4-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-344">TABLE_OWNER</span></span>|<span data-ttu-id="f9ef4-345">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-345">String</span></span>|  
|<span data-ttu-id="f9ef4-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-346">TABLE_NAME</span></span>|<span data-ttu-id="f9ef4-347">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-347">String</span></span>|  
|<span data-ttu-id="f9ef4-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-348">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-349">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-349">String</span></span>|  
|<span data-ttu-id="f9ef4-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-350">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-351">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-351">Int16</span></span>|  
|<span data-ttu-id="f9ef4-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-352">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-353">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-353">String</span></span>|  
|<span data-ttu-id="f9ef4-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-354">PRECISION</span></span>|<span data-ttu-id="f9ef4-355">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-355">Int32</span></span>|  
|<span data-ttu-id="f9ef4-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-356">LENGTH</span></span>|<span data-ttu-id="f9ef4-357">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-357">Int32</span></span>|  
|<span data-ttu-id="f9ef4-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-358">SCALE</span></span>|<span data-ttu-id="f9ef4-359">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-359">Int16</span></span>|  
|<span data-ttu-id="f9ef4-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-360">RADIX</span></span>|<span data-ttu-id="f9ef4-361">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-361">Int16</span></span>|  
|<span data-ttu-id="f9ef4-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-362">NULLABLE</span></span>|<span data-ttu-id="f9ef4-363">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-363">Int16</span></span>|  
|<span data-ttu-id="f9ef4-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-364">REMARKS</span></span>|<span data-ttu-id="f9ef4-365">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-365">String</span></span>|  
|<span data-ttu-id="f9ef4-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-367">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f9ef4-368">程序</span><span class="sxs-lookup"><span data-stu-id="f9ef4-368">Procedures</span></span>  
  
|<span data-ttu-id="f9ef4-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-369">ColumnName</span></span>|<span data-ttu-id="f9ef4-370">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-372">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-372">String</span></span>|  
|<span data-ttu-id="f9ef4-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f9ef4-374">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-374">String</span></span>|  
|<span data-ttu-id="f9ef4-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-376">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-376">String</span></span>|  
|<span data-ttu-id="f9ef4-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f9ef4-378">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-378">Int16</span></span>|  
|<span data-ttu-id="f9ef4-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f9ef4-380">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-380">Int16</span></span>|  
|<span data-ttu-id="f9ef4-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f9ef4-382">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-382">Int16</span></span>|  
|<span data-ttu-id="f9ef4-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-383">REMARKS</span></span>|<span data-ttu-id="f9ef4-384">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-384">String</span></span>|  
|<span data-ttu-id="f9ef4-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f9ef4-386">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f9ef4-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f9ef4-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f9ef4-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-388">ColumnName</span></span>|<span data-ttu-id="f9ef4-389">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-391">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-391">String</span></span>|  
|<span data-ttu-id="f9ef4-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f9ef4-393">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-393">String</span></span>|  
|<span data-ttu-id="f9ef4-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-395">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-395">String</span></span>|  
|<span data-ttu-id="f9ef4-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-396">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-397">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-397">String</span></span>|  
|<span data-ttu-id="f9ef4-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-398">COLUMN_TYPE</span></span>|<span data-ttu-id="f9ef4-399">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-399">Int16</span></span>|  
|<span data-ttu-id="f9ef4-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-400">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-401">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-401">Int16</span></span>|  
|<span data-ttu-id="f9ef4-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-402">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-403">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-403">String</span></span>|  
|<span data-ttu-id="f9ef4-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-404">PRECISION</span></span>|<span data-ttu-id="f9ef4-405">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-405">Int32</span></span>|  
|<span data-ttu-id="f9ef4-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-406">LENGTH</span></span>|<span data-ttu-id="f9ef4-407">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-407">Int32</span></span>|  
|<span data-ttu-id="f9ef4-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-408">SCALE</span></span>|<span data-ttu-id="f9ef4-409">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-409">Int16</span></span>|  
|<span data-ttu-id="f9ef4-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-410">RADIX</span></span>|<span data-ttu-id="f9ef4-411">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-411">Int16</span></span>|  
|<span data-ttu-id="f9ef4-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-412">NULLABLE</span></span>|<span data-ttu-id="f9ef4-413">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-413">Int16</span></span>|  
|<span data-ttu-id="f9ef4-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-414">REMARKS</span></span>|<span data-ttu-id="f9ef4-415">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-415">String</span></span>|  
|<span data-ttu-id="f9ef4-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="f9ef4-416">OVERLOAD</span></span>|<span data-ttu-id="f9ef4-417">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-417">Int32</span></span>|  
|<span data-ttu-id="f9ef4-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-419">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="f9ef4-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="f9ef4-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="f9ef4-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="f9ef4-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f9ef4-422">資料表</span><span class="sxs-lookup"><span data-stu-id="f9ef4-422">Tables</span></span>  
  
-   <span data-ttu-id="f9ef4-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="f9ef4-423">Indexes</span></span>  
  
-   <span data-ttu-id="f9ef4-424">資料行</span><span class="sxs-lookup"><span data-stu-id="f9ef4-424">Columns</span></span>  
  
-   <span data-ttu-id="f9ef4-425">程序</span><span class="sxs-lookup"><span data-stu-id="f9ef4-425">Procedures</span></span>  
  
-   <span data-ttu-id="f9ef4-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f9ef4-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f9ef4-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f9ef4-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f9ef4-428">檢視</span><span class="sxs-lookup"><span data-stu-id="f9ef4-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f9ef4-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="f9ef4-429">Tables and Views</span></span>  
  
|<span data-ttu-id="f9ef4-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-430">ColumnName</span></span>|<span data-ttu-id="f9ef4-431">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-433">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-433">String</span></span>|  
|<span data-ttu-id="f9ef4-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-434">TABLE_OWNER</span></span>|<span data-ttu-id="f9ef4-435">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-435">String</span></span>|  
|<span data-ttu-id="f9ef4-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-436">TABLE_NAME</span></span>|<span data-ttu-id="f9ef4-437">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-437">String</span></span>|  
|<span data-ttu-id="f9ef4-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-438">TABLE_TYPE</span></span>|<span data-ttu-id="f9ef4-439">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-439">String</span></span>|  
|<span data-ttu-id="f9ef4-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-440">REMARKS</span></span>|<span data-ttu-id="f9ef4-441">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f9ef4-442">資料行</span><span class="sxs-lookup"><span data-stu-id="f9ef4-442">Columns</span></span>  
  
|<span data-ttu-id="f9ef4-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-443">ColumnName</span></span>|<span data-ttu-id="f9ef4-444">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-446">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-446">String</span></span>|  
|<span data-ttu-id="f9ef4-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-447">TABLE_OWNER</span></span>|<span data-ttu-id="f9ef4-448">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-448">String</span></span>|  
|<span data-ttu-id="f9ef4-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-449">TABLE_NAME</span></span>|<span data-ttu-id="f9ef4-450">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-450">String</span></span>|  
|<span data-ttu-id="f9ef4-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-451">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-452">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-452">String</span></span>|  
|<span data-ttu-id="f9ef4-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-453">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-454">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-454">Int16</span></span>|  
|<span data-ttu-id="f9ef4-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-455">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-456">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-456">String</span></span>|  
|<span data-ttu-id="f9ef4-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-457">PRECISION</span></span>|<span data-ttu-id="f9ef4-458">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-458">Int32</span></span>|  
|<span data-ttu-id="f9ef4-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-459">LENGTH</span></span>|<span data-ttu-id="f9ef4-460">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-460">Int32</span></span>|  
|<span data-ttu-id="f9ef4-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-461">SCALE</span></span>|<span data-ttu-id="f9ef4-462">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-462">Int16</span></span>|  
|<span data-ttu-id="f9ef4-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-463">RADIX</span></span>|<span data-ttu-id="f9ef4-464">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-464">Int16</span></span>|  
|<span data-ttu-id="f9ef4-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-465">NULLABLE</span></span>|<span data-ttu-id="f9ef4-466">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-466">Int16</span></span>|  
|<span data-ttu-id="f9ef4-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-467">REMARKS</span></span>|<span data-ttu-id="f9ef4-468">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-468">String</span></span>|  
|<span data-ttu-id="f9ef4-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-470">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f9ef4-471">程序</span><span class="sxs-lookup"><span data-stu-id="f9ef4-471">Procedures</span></span>  
  
|<span data-ttu-id="f9ef4-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-472">ColumnName</span></span>|<span data-ttu-id="f9ef4-473">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-475">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-475">String</span></span>|  
|<span data-ttu-id="f9ef4-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f9ef4-477">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-477">String</span></span>|  
|<span data-ttu-id="f9ef4-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-479">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-479">String</span></span>|  
|<span data-ttu-id="f9ef4-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f9ef4-481">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-481">Int16</span></span>|  
|<span data-ttu-id="f9ef4-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f9ef4-483">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-483">Int16</span></span>|  
|<span data-ttu-id="f9ef4-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f9ef4-485">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-485">Int16</span></span>|  
|<span data-ttu-id="f9ef4-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-486">REMARKS</span></span>|<span data-ttu-id="f9ef4-487">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-487">String</span></span>|  
|<span data-ttu-id="f9ef4-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f9ef4-489">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f9ef4-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f9ef4-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f9ef4-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-491">ColumnName</span></span>|<span data-ttu-id="f9ef4-492">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f9ef4-494">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-494">String</span></span>|  
|<span data-ttu-id="f9ef4-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9ef4-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f9ef4-496">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-496">String</span></span>|  
|<span data-ttu-id="f9ef4-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-498">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-498">String</span></span>|  
|<span data-ttu-id="f9ef4-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-499">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-500">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-500">String</span></span>|  
|<span data-ttu-id="f9ef4-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-501">COLUMN_TYPE</span></span>|<span data-ttu-id="f9ef4-502">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-502">Int16</span></span>|  
|<span data-ttu-id="f9ef4-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-503">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-504">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-504">Int16</span></span>|  
|<span data-ttu-id="f9ef4-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-505">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-506">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-506">String</span></span>|  
|<span data-ttu-id="f9ef4-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-507">PRECISION</span></span>|<span data-ttu-id="f9ef4-508">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-508">Int32</span></span>|  
|<span data-ttu-id="f9ef4-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-509">LENGTH</span></span>|<span data-ttu-id="f9ef4-510">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-510">Int32</span></span>|  
|<span data-ttu-id="f9ef4-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-511">SCALE</span></span>|<span data-ttu-id="f9ef4-512">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-512">Int16</span></span>|  
|<span data-ttu-id="f9ef4-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-513">RADIX</span></span>|<span data-ttu-id="f9ef4-514">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-514">Int16</span></span>|  
|<span data-ttu-id="f9ef4-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-515">NULLABLE</span></span>|<span data-ttu-id="f9ef4-516">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-516">Int16</span></span>|  
|<span data-ttu-id="f9ef4-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-517">REMARKS</span></span>|<span data-ttu-id="f9ef4-518">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-518">String</span></span>|  
|<span data-ttu-id="f9ef4-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="f9ef4-519">OVERLOAD</span></span>|<span data-ttu-id="f9ef4-520">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-520">Int32</span></span>|  
|<span data-ttu-id="f9ef4-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-522">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f9ef4-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f9ef4-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f9ef4-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f9ef4-524">ColumnName</span></span>|<span data-ttu-id="f9ef4-525">DataType</span><span class="sxs-lookup"><span data-stu-id="f9ef4-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f9ef4-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f9ef4-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="f9ef4-527">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-527">String</span></span>|  
|<span data-ttu-id="f9ef4-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f9ef4-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f9ef4-529">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-529">String</span></span>|  
|<span data-ttu-id="f9ef4-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="f9ef4-531">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-531">String</span></span>|  
|<span data-ttu-id="f9ef4-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-532">COLUMN_NAME</span></span>|<span data-ttu-id="f9ef4-533">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-533">String</span></span>|  
|<span data-ttu-id="f9ef4-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-534">COLUMN_TYPE</span></span>|<span data-ttu-id="f9ef4-535">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-535">Int16</span></span>|  
|<span data-ttu-id="f9ef4-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-536">DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-537">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-537">Int16</span></span>|  
|<span data-ttu-id="f9ef4-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9ef4-538">TYPE_NAME</span></span>|<span data-ttu-id="f9ef4-539">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-539">String</span></span>|  
|<span data-ttu-id="f9ef4-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-540">COLUMN_SIZE</span></span>|<span data-ttu-id="f9ef4-541">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-541">Int32</span></span>|  
|<span data-ttu-id="f9ef4-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="f9ef4-543">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-543">Int32</span></span>|  
|<span data-ttu-id="f9ef4-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f9ef4-545">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-545">Int16</span></span>|  
|<span data-ttu-id="f9ef4-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f9ef4-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f9ef4-547">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-547">Int16</span></span>|  
|<span data-ttu-id="f9ef4-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-548">NULLABLE</span></span>|<span data-ttu-id="f9ef4-549">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-549">Int16</span></span>|  
|<span data-ttu-id="f9ef4-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f9ef4-550">REMARKS</span></span>|<span data-ttu-id="f9ef4-551">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-551">String</span></span>|  
|<span data-ttu-id="f9ef4-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f9ef4-552">COLUMN_DEF</span></span>|<span data-ttu-id="f9ef4-553">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-553">String</span></span>|  
|<span data-ttu-id="f9ef4-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f9ef4-555">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-555">Int16</span></span>|  
|<span data-ttu-id="f9ef4-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f9ef4-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f9ef4-557">Int16</span><span class="sxs-lookup"><span data-stu-id="f9ef4-557">Int16</span></span>|  
|<span data-ttu-id="f9ef4-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f9ef4-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f9ef4-559">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-559">Int32</span></span>|  
|<span data-ttu-id="f9ef4-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f9ef4-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="f9ef4-561">Int32</span><span class="sxs-lookup"><span data-stu-id="f9ef4-561">Int32</span></span>|  
|<span data-ttu-id="f9ef4-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f9ef4-562">IS_NULLABLE</span></span>|<span data-ttu-id="f9ef4-563">String</span><span class="sxs-lookup"><span data-stu-id="f9ef4-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9ef4-564">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9ef4-564">See Also</span></span>  
 [<span data-ttu-id="f9ef4-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="f9ef4-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
