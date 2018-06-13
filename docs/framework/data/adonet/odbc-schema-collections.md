---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 36d0859b897bfcea33803c219ade14722ed90421
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766643"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="b0875-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="b0875-102">ODBC Schema Collections</span></span>
<span data-ttu-id="b0875-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="b0875-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="b0875-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="b0875-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="b0875-105">Microsoft SQL Server ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="b0875-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b0875-106">資料表</span><span class="sxs-lookup"><span data-stu-id="b0875-106">Tables</span></span>  
  
-   <span data-ttu-id="b0875-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="b0875-107">Indexes</span></span>  
  
-   <span data-ttu-id="b0875-108">資料行</span><span class="sxs-lookup"><span data-stu-id="b0875-108">Columns</span></span>  
  
-   <span data-ttu-id="b0875-109">程序</span><span class="sxs-lookup"><span data-stu-id="b0875-109">Procedures</span></span>  
  
-   <span data-ttu-id="b0875-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b0875-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b0875-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b0875-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b0875-112">檢視</span><span class="sxs-lookup"><span data-stu-id="b0875-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b0875-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="b0875-113">Tables and Views</span></span>  
  
|<span data-ttu-id="b0875-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-114">ColumnName</span></span>|<span data-ttu-id="b0875-115">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b0875-116">TABLE_CAT</span></span>|<span data-ttu-id="b0875-117">String</span><span class="sxs-lookup"><span data-stu-id="b0875-117">String</span></span>|  
|<span data-ttu-id="b0875-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b0875-118">TABLE_SCHEM</span></span>|<span data-ttu-id="b0875-119">String</span><span class="sxs-lookup"><span data-stu-id="b0875-119">String</span></span>|  
|<span data-ttu-id="b0875-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-120">TABLE_NAME</span></span>|<span data-ttu-id="b0875-121">String</span><span class="sxs-lookup"><span data-stu-id="b0875-121">String</span></span>|  
|<span data-ttu-id="b0875-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-122">TABLE_TYPE</span></span>|<span data-ttu-id="b0875-123">String</span><span class="sxs-lookup"><span data-stu-id="b0875-123">String</span></span>|  
|<span data-ttu-id="b0875-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-124">REMARKS</span></span>|<span data-ttu-id="b0875-125">String</span><span class="sxs-lookup"><span data-stu-id="b0875-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b0875-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="b0875-126">Indexes</span></span>  
  
|<span data-ttu-id="b0875-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-127">ColumnName</span></span>|<span data-ttu-id="b0875-128">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b0875-129">TABLE_CAT</span></span>|<span data-ttu-id="b0875-130">String</span><span class="sxs-lookup"><span data-stu-id="b0875-130">String</span></span>|  
|<span data-ttu-id="b0875-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b0875-131">TABLE_SCHEM</span></span>|<span data-ttu-id="b0875-132">String</span><span class="sxs-lookup"><span data-stu-id="b0875-132">String</span></span>|  
|<span data-ttu-id="b0875-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-133">TABLE_NAME</span></span>|<span data-ttu-id="b0875-134">String</span><span class="sxs-lookup"><span data-stu-id="b0875-134">String</span></span>|  
|<span data-ttu-id="b0875-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b0875-135">NON_UNIQUE</span></span>|<span data-ttu-id="b0875-136">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-136">Int16</span></span>|  
|<span data-ttu-id="b0875-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="b0875-138">String</span><span class="sxs-lookup"><span data-stu-id="b0875-138">String</span></span>|  
|<span data-ttu-id="b0875-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-139">INDEX_NAME</span></span>|<span data-ttu-id="b0875-140">String</span><span class="sxs-lookup"><span data-stu-id="b0875-140">String</span></span>|  
|<span data-ttu-id="b0875-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-141">TYPE</span></span>|<span data-ttu-id="b0875-142">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-142">Int16</span></span>|  
|<span data-ttu-id="b0875-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-144">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-144">Int16</span></span>|  
|<span data-ttu-id="b0875-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-145">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-146">String</span><span class="sxs-lookup"><span data-stu-id="b0875-146">String</span></span>|  
|<span data-ttu-id="b0875-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="b0875-147">ASC_OR_DESC</span></span>|<span data-ttu-id="b0875-148">String</span><span class="sxs-lookup"><span data-stu-id="b0875-148">String</span></span>|  
|<span data-ttu-id="b0875-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="b0875-149">CARDINATLITY</span></span>|<span data-ttu-id="b0875-150">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-150">Int32</span></span>|  
|<span data-ttu-id="b0875-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="b0875-151">PAGES</span></span>|<span data-ttu-id="b0875-152">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-152">Int32</span></span>|  
|<span data-ttu-id="b0875-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b0875-153">FILTER_CONDITION</span></span>|<span data-ttu-id="b0875-154">String</span><span class="sxs-lookup"><span data-stu-id="b0875-154">String</span></span>|  
|<span data-ttu-id="b0875-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b0875-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b0875-156">String</span><span class="sxs-lookup"><span data-stu-id="b0875-156">String</span></span>|  
|<span data-ttu-id="b0875-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="b0875-158">Byte</span><span class="sxs-lookup"><span data-stu-id="b0875-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b0875-159">資料行</span><span class="sxs-lookup"><span data-stu-id="b0875-159">Columns</span></span>  
  
|<span data-ttu-id="b0875-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-160">ColumnName</span></span>|<span data-ttu-id="b0875-161">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b0875-162">TABLE_CAT</span></span>|<span data-ttu-id="b0875-163">String</span><span class="sxs-lookup"><span data-stu-id="b0875-163">String</span></span>|  
|<span data-ttu-id="b0875-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b0875-164">TABLE_SCHEM</span></span>|<span data-ttu-id="b0875-165">String</span><span class="sxs-lookup"><span data-stu-id="b0875-165">String</span></span>|  
|<span data-ttu-id="b0875-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-166">TABLE_NAME</span></span>|<span data-ttu-id="b0875-167">String</span><span class="sxs-lookup"><span data-stu-id="b0875-167">String</span></span>|  
|<span data-ttu-id="b0875-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-168">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-169">String</span><span class="sxs-lookup"><span data-stu-id="b0875-169">String</span></span>|  
|<span data-ttu-id="b0875-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-170">DATA_TYPE</span></span>|<span data-ttu-id="b0875-171">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-171">Int16</span></span>|  
|<span data-ttu-id="b0875-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-172">TYPE_NAME</span></span>|<span data-ttu-id="b0875-173">String</span><span class="sxs-lookup"><span data-stu-id="b0875-173">String</span></span>|  
|<span data-ttu-id="b0875-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b0875-174">COLUMN_SIZE</span></span>|<span data-ttu-id="b0875-175">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-175">Int32</span></span>|  
|<span data-ttu-id="b0875-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="b0875-177">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-177">Int32</span></span>|  
|<span data-ttu-id="b0875-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b0875-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b0875-179">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-179">Int16</span></span>|  
|<span data-ttu-id="b0875-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b0875-181">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-181">Int16</span></span>|  
|<span data-ttu-id="b0875-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-182">NULLABLE</span></span>|<span data-ttu-id="b0875-183">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-183">Int16</span></span>|  
|<span data-ttu-id="b0875-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-184">REMARKS</span></span>|<span data-ttu-id="b0875-185">String</span><span class="sxs-lookup"><span data-stu-id="b0875-185">String</span></span>|  
|<span data-ttu-id="b0875-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b0875-186">COLUMN_DEF</span></span>|<span data-ttu-id="b0875-187">String</span><span class="sxs-lookup"><span data-stu-id="b0875-187">String</span></span>|  
|<span data-ttu-id="b0875-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b0875-189">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-189">Int16</span></span>|  
|<span data-ttu-id="b0875-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b0875-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b0875-191">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-191">Int16</span></span>|  
|<span data-ttu-id="b0875-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b0875-193">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-193">Int32</span></span>|  
|<span data-ttu-id="b0875-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-195">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-195">Int32</span></span>|  
|<span data-ttu-id="b0875-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-196">IS_NULLABLE</span></span>|<span data-ttu-id="b0875-197">String</span><span class="sxs-lookup"><span data-stu-id="b0875-197">String</span></span>|  
|<span data-ttu-id="b0875-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b0875-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b0875-199">String</span><span class="sxs-lookup"><span data-stu-id="b0875-199">String</span></span>|  
|<span data-ttu-id="b0875-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b0875-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b0875-201">String</span><span class="sxs-lookup"><span data-stu-id="b0875-201">String</span></span>|  
|<span data-ttu-id="b0875-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="b0875-203">Byte</span><span class="sxs-lookup"><span data-stu-id="b0875-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b0875-204">程序</span><span class="sxs-lookup"><span data-stu-id="b0875-204">Procedures</span></span>  
  
|<span data-ttu-id="b0875-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-205">ColumnName</span></span>|<span data-ttu-id="b0875-206">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b0875-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="b0875-208">String</span><span class="sxs-lookup"><span data-stu-id="b0875-208">String</span></span>|  
|<span data-ttu-id="b0875-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b0875-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b0875-210">String</span><span class="sxs-lookup"><span data-stu-id="b0875-210">String</span></span>|  
|<span data-ttu-id="b0875-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-212">String</span><span class="sxs-lookup"><span data-stu-id="b0875-212">String</span></span>|  
|<span data-ttu-id="b0875-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b0875-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b0875-214">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-214">Int32</span></span>|  
|<span data-ttu-id="b0875-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b0875-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b0875-216">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-216">Int32</span></span>|  
|<span data-ttu-id="b0875-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b0875-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b0875-218">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-218">Int32</span></span>|  
|<span data-ttu-id="b0875-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-219">REMARKS</span></span>|<span data-ttu-id="b0875-220">String</span><span class="sxs-lookup"><span data-stu-id="b0875-220">String</span></span>|  
|<span data-ttu-id="b0875-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b0875-222">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b0875-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b0875-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b0875-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-224">ColumnName</span></span>|<span data-ttu-id="b0875-225">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b0875-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="b0875-227">String</span><span class="sxs-lookup"><span data-stu-id="b0875-227">String</span></span>|  
|<span data-ttu-id="b0875-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b0875-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b0875-229">String</span><span class="sxs-lookup"><span data-stu-id="b0875-229">String</span></span>|  
|<span data-ttu-id="b0875-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-231">String</span><span class="sxs-lookup"><span data-stu-id="b0875-231">String</span></span>|  
|<span data-ttu-id="b0875-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-232">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-233">String</span><span class="sxs-lookup"><span data-stu-id="b0875-233">String</span></span>|  
|<span data-ttu-id="b0875-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-234">COLUMN_TYPE</span></span>|<span data-ttu-id="b0875-235">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-235">Int16</span></span>|  
|<span data-ttu-id="b0875-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-236">DATA_TYPE</span></span>|<span data-ttu-id="b0875-237">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-237">Int16</span></span>|  
|<span data-ttu-id="b0875-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-238">TYPE_NAME</span></span>|<span data-ttu-id="b0875-239">String</span><span class="sxs-lookup"><span data-stu-id="b0875-239">String</span></span>|  
|<span data-ttu-id="b0875-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b0875-240">COLUMN_SIZE</span></span>|<span data-ttu-id="b0875-241">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-241">Int32</span></span>|  
|<span data-ttu-id="b0875-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="b0875-243">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-243">Int32</span></span>|  
|<span data-ttu-id="b0875-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b0875-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b0875-245">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-245">Int16</span></span>|  
|<span data-ttu-id="b0875-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b0875-247">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-247">Int16</span></span>|  
|<span data-ttu-id="b0875-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-248">NULLABLE</span></span>|<span data-ttu-id="b0875-249">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-249">Int16</span></span>|  
|<span data-ttu-id="b0875-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-250">REMARKS</span></span>|<span data-ttu-id="b0875-251">String</span><span class="sxs-lookup"><span data-stu-id="b0875-251">String</span></span>|  
|<span data-ttu-id="b0875-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b0875-252">COLUMN_DEF</span></span>|<span data-ttu-id="b0875-253">String</span><span class="sxs-lookup"><span data-stu-id="b0875-253">String</span></span>|  
|<span data-ttu-id="b0875-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b0875-255">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-255">Int16</span></span>|  
|<span data-ttu-id="b0875-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b0875-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b0875-257">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-257">Int16</span></span>|  
|<span data-ttu-id="b0875-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b0875-259">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-259">Int32</span></span>|  
|<span data-ttu-id="b0875-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-261">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-261">Int32</span></span>|  
|<span data-ttu-id="b0875-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-262">IS_NULLABLE</span></span>|<span data-ttu-id="b0875-263">String</span><span class="sxs-lookup"><span data-stu-id="b0875-263">String</span></span>|  
|<span data-ttu-id="b0875-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b0875-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b0875-265">String</span><span class="sxs-lookup"><span data-stu-id="b0875-265">String</span></span>|  
|<span data-ttu-id="b0875-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b0875-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b0875-267">String</span><span class="sxs-lookup"><span data-stu-id="b0875-267">String</span></span>|  
|<span data-ttu-id="b0875-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="b0875-269">Byte</span><span class="sxs-lookup"><span data-stu-id="b0875-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b0875-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b0875-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b0875-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-271">ColumnName</span></span>|<span data-ttu-id="b0875-272">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b0875-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="b0875-274">String</span><span class="sxs-lookup"><span data-stu-id="b0875-274">String</span></span>|  
|<span data-ttu-id="b0875-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b0875-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b0875-276">String</span><span class="sxs-lookup"><span data-stu-id="b0875-276">String</span></span>|  
|<span data-ttu-id="b0875-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-278">String</span><span class="sxs-lookup"><span data-stu-id="b0875-278">String</span></span>|  
|<span data-ttu-id="b0875-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-279">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-280">String</span><span class="sxs-lookup"><span data-stu-id="b0875-280">String</span></span>|  
|<span data-ttu-id="b0875-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-281">COLUMN_TYPE</span></span>|<span data-ttu-id="b0875-282">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-282">Int16</span></span>|  
|<span data-ttu-id="b0875-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-283">DATA_TYPE</span></span>|<span data-ttu-id="b0875-284">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-284">Int16</span></span>|  
|<span data-ttu-id="b0875-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-285">TYPE_NAME</span></span>|<span data-ttu-id="b0875-286">String</span><span class="sxs-lookup"><span data-stu-id="b0875-286">String</span></span>|  
|<span data-ttu-id="b0875-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b0875-287">COLUMN_SIZE</span></span>|<span data-ttu-id="b0875-288">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-288">Int32</span></span>|  
|<span data-ttu-id="b0875-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="b0875-290">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-290">Int32</span></span>|  
|<span data-ttu-id="b0875-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b0875-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b0875-292">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-292">Int16</span></span>|  
|<span data-ttu-id="b0875-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b0875-294">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-294">Int16</span></span>|  
|<span data-ttu-id="b0875-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-295">NULLABLE</span></span>|<span data-ttu-id="b0875-296">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-296">Int16</span></span>|  
|<span data-ttu-id="b0875-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-297">REMARKS</span></span>|<span data-ttu-id="b0875-298">String</span><span class="sxs-lookup"><span data-stu-id="b0875-298">String</span></span>|  
|<span data-ttu-id="b0875-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b0875-299">COLUMN_DEF</span></span>|<span data-ttu-id="b0875-300">String</span><span class="sxs-lookup"><span data-stu-id="b0875-300">String</span></span>|  
|<span data-ttu-id="b0875-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b0875-302">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-302">Int16</span></span>|  
|<span data-ttu-id="b0875-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b0875-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b0875-304">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-304">Int16</span></span>|  
|<span data-ttu-id="b0875-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b0875-306">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-306">Int32</span></span>|  
|<span data-ttu-id="b0875-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-308">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-308">Int32</span></span>|  
|<span data-ttu-id="b0875-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-309">IS_NULLABLE</span></span>|<span data-ttu-id="b0875-310">String</span><span class="sxs-lookup"><span data-stu-id="b0875-310">String</span></span>|  
|<span data-ttu-id="b0875-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b0875-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b0875-312">String</span><span class="sxs-lookup"><span data-stu-id="b0875-312">String</span></span>|  
|<span data-ttu-id="b0875-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b0875-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b0875-314">String</span><span class="sxs-lookup"><span data-stu-id="b0875-314">String</span></span>|  
|<span data-ttu-id="b0875-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="b0875-316">Byte</span><span class="sxs-lookup"><span data-stu-id="b0875-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="b0875-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="b0875-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="b0875-318">Microsoft SQL Server Oracle ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="b0875-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b0875-319">資料表</span><span class="sxs-lookup"><span data-stu-id="b0875-319">Tables</span></span>  
  
-   <span data-ttu-id="b0875-320">資料行</span><span class="sxs-lookup"><span data-stu-id="b0875-320">Columns</span></span>  
  
-   <span data-ttu-id="b0875-321">程序</span><span class="sxs-lookup"><span data-stu-id="b0875-321">Procedures</span></span>  
  
-   <span data-ttu-id="b0875-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b0875-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b0875-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b0875-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b0875-324">檢視</span><span class="sxs-lookup"><span data-stu-id="b0875-324">Views</span></span>  
  
-   <span data-ttu-id="b0875-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="b0875-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b0875-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="b0875-326">Tables and Views</span></span>  
  
|<span data-ttu-id="b0875-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-327">ColumnName</span></span>|<span data-ttu-id="b0875-328">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b0875-330">String</span><span class="sxs-lookup"><span data-stu-id="b0875-330">String</span></span>|  
|<span data-ttu-id="b0875-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-331">TABLE_OWNER</span></span>|<span data-ttu-id="b0875-332">String</span><span class="sxs-lookup"><span data-stu-id="b0875-332">String</span></span>|  
|<span data-ttu-id="b0875-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-333">TABLE_NAME</span></span>|<span data-ttu-id="b0875-334">String</span><span class="sxs-lookup"><span data-stu-id="b0875-334">String</span></span>|  
|<span data-ttu-id="b0875-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-335">TABLE_TYPE</span></span>|<span data-ttu-id="b0875-336">String</span><span class="sxs-lookup"><span data-stu-id="b0875-336">String</span></span>|  
|<span data-ttu-id="b0875-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-337">REMARKS</span></span>|<span data-ttu-id="b0875-338">String</span><span class="sxs-lookup"><span data-stu-id="b0875-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b0875-339">資料行</span><span class="sxs-lookup"><span data-stu-id="b0875-339">Columns</span></span>  
  
|<span data-ttu-id="b0875-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-340">ColumnName</span></span>|<span data-ttu-id="b0875-341">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b0875-343">String</span><span class="sxs-lookup"><span data-stu-id="b0875-343">String</span></span>|  
|<span data-ttu-id="b0875-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-344">TABLE_OWNER</span></span>|<span data-ttu-id="b0875-345">String</span><span class="sxs-lookup"><span data-stu-id="b0875-345">String</span></span>|  
|<span data-ttu-id="b0875-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-346">TABLE_NAME</span></span>|<span data-ttu-id="b0875-347">String</span><span class="sxs-lookup"><span data-stu-id="b0875-347">String</span></span>|  
|<span data-ttu-id="b0875-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-348">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-349">String</span><span class="sxs-lookup"><span data-stu-id="b0875-349">String</span></span>|  
|<span data-ttu-id="b0875-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-350">DATA_TYPE</span></span>|<span data-ttu-id="b0875-351">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-351">Int16</span></span>|  
|<span data-ttu-id="b0875-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-352">TYPE_NAME</span></span>|<span data-ttu-id="b0875-353">String</span><span class="sxs-lookup"><span data-stu-id="b0875-353">String</span></span>|  
|<span data-ttu-id="b0875-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b0875-354">PRECISION</span></span>|<span data-ttu-id="b0875-355">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-355">Int32</span></span>|  
|<span data-ttu-id="b0875-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-356">LENGTH</span></span>|<span data-ttu-id="b0875-357">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-357">Int32</span></span>|  
|<span data-ttu-id="b0875-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="b0875-358">SCALE</span></span>|<span data-ttu-id="b0875-359">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-359">Int16</span></span>|  
|<span data-ttu-id="b0875-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-360">RADIX</span></span>|<span data-ttu-id="b0875-361">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-361">Int16</span></span>|  
|<span data-ttu-id="b0875-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-362">NULLABLE</span></span>|<span data-ttu-id="b0875-363">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-363">Int16</span></span>|  
|<span data-ttu-id="b0875-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-364">REMARKS</span></span>|<span data-ttu-id="b0875-365">String</span><span class="sxs-lookup"><span data-stu-id="b0875-365">String</span></span>|  
|<span data-ttu-id="b0875-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-367">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b0875-368">程序</span><span class="sxs-lookup"><span data-stu-id="b0875-368">Procedures</span></span>  
  
|<span data-ttu-id="b0875-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-369">ColumnName</span></span>|<span data-ttu-id="b0875-370">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b0875-372">String</span><span class="sxs-lookup"><span data-stu-id="b0875-372">String</span></span>|  
|<span data-ttu-id="b0875-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b0875-374">String</span><span class="sxs-lookup"><span data-stu-id="b0875-374">String</span></span>|  
|<span data-ttu-id="b0875-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-376">String</span><span class="sxs-lookup"><span data-stu-id="b0875-376">String</span></span>|  
|<span data-ttu-id="b0875-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b0875-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b0875-378">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-378">Int16</span></span>|  
|<span data-ttu-id="b0875-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b0875-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b0875-380">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-380">Int16</span></span>|  
|<span data-ttu-id="b0875-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b0875-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b0875-382">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-382">Int16</span></span>|  
|<span data-ttu-id="b0875-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-383">REMARKS</span></span>|<span data-ttu-id="b0875-384">String</span><span class="sxs-lookup"><span data-stu-id="b0875-384">String</span></span>|  
|<span data-ttu-id="b0875-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b0875-386">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b0875-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b0875-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b0875-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-388">ColumnName</span></span>|<span data-ttu-id="b0875-389">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b0875-391">String</span><span class="sxs-lookup"><span data-stu-id="b0875-391">String</span></span>|  
|<span data-ttu-id="b0875-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b0875-393">String</span><span class="sxs-lookup"><span data-stu-id="b0875-393">String</span></span>|  
|<span data-ttu-id="b0875-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-395">String</span><span class="sxs-lookup"><span data-stu-id="b0875-395">String</span></span>|  
|<span data-ttu-id="b0875-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-396">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-397">String</span><span class="sxs-lookup"><span data-stu-id="b0875-397">String</span></span>|  
|<span data-ttu-id="b0875-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-398">COLUMN_TYPE</span></span>|<span data-ttu-id="b0875-399">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-399">Int16</span></span>|  
|<span data-ttu-id="b0875-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-400">DATA_TYPE</span></span>|<span data-ttu-id="b0875-401">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-401">Int16</span></span>|  
|<span data-ttu-id="b0875-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-402">TYPE_NAME</span></span>|<span data-ttu-id="b0875-403">String</span><span class="sxs-lookup"><span data-stu-id="b0875-403">String</span></span>|  
|<span data-ttu-id="b0875-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b0875-404">PRECISION</span></span>|<span data-ttu-id="b0875-405">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-405">Int32</span></span>|  
|<span data-ttu-id="b0875-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-406">LENGTH</span></span>|<span data-ttu-id="b0875-407">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-407">Int32</span></span>|  
|<span data-ttu-id="b0875-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="b0875-408">SCALE</span></span>|<span data-ttu-id="b0875-409">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-409">Int16</span></span>|  
|<span data-ttu-id="b0875-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-410">RADIX</span></span>|<span data-ttu-id="b0875-411">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-411">Int16</span></span>|  
|<span data-ttu-id="b0875-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-412">NULLABLE</span></span>|<span data-ttu-id="b0875-413">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-413">Int16</span></span>|  
|<span data-ttu-id="b0875-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-414">REMARKS</span></span>|<span data-ttu-id="b0875-415">String</span><span class="sxs-lookup"><span data-stu-id="b0875-415">String</span></span>|  
|<span data-ttu-id="b0875-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="b0875-416">OVERLOAD</span></span>|<span data-ttu-id="b0875-417">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-417">Int32</span></span>|  
|<span data-ttu-id="b0875-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-419">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="b0875-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="b0875-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="b0875-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="b0875-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b0875-422">資料表</span><span class="sxs-lookup"><span data-stu-id="b0875-422">Tables</span></span>  
  
-   <span data-ttu-id="b0875-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="b0875-423">Indexes</span></span>  
  
-   <span data-ttu-id="b0875-424">資料行</span><span class="sxs-lookup"><span data-stu-id="b0875-424">Columns</span></span>  
  
-   <span data-ttu-id="b0875-425">程序</span><span class="sxs-lookup"><span data-stu-id="b0875-425">Procedures</span></span>  
  
-   <span data-ttu-id="b0875-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b0875-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b0875-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b0875-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b0875-428">檢視</span><span class="sxs-lookup"><span data-stu-id="b0875-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b0875-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="b0875-429">Tables and Views</span></span>  
  
|<span data-ttu-id="b0875-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-430">ColumnName</span></span>|<span data-ttu-id="b0875-431">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b0875-433">String</span><span class="sxs-lookup"><span data-stu-id="b0875-433">String</span></span>|  
|<span data-ttu-id="b0875-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-434">TABLE_OWNER</span></span>|<span data-ttu-id="b0875-435">String</span><span class="sxs-lookup"><span data-stu-id="b0875-435">String</span></span>|  
|<span data-ttu-id="b0875-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-436">TABLE_NAME</span></span>|<span data-ttu-id="b0875-437">String</span><span class="sxs-lookup"><span data-stu-id="b0875-437">String</span></span>|  
|<span data-ttu-id="b0875-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-438">TABLE_TYPE</span></span>|<span data-ttu-id="b0875-439">String</span><span class="sxs-lookup"><span data-stu-id="b0875-439">String</span></span>|  
|<span data-ttu-id="b0875-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-440">REMARKS</span></span>|<span data-ttu-id="b0875-441">String</span><span class="sxs-lookup"><span data-stu-id="b0875-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b0875-442">資料行</span><span class="sxs-lookup"><span data-stu-id="b0875-442">Columns</span></span>  
  
|<span data-ttu-id="b0875-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-443">ColumnName</span></span>|<span data-ttu-id="b0875-444">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b0875-446">String</span><span class="sxs-lookup"><span data-stu-id="b0875-446">String</span></span>|  
|<span data-ttu-id="b0875-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-447">TABLE_OWNER</span></span>|<span data-ttu-id="b0875-448">String</span><span class="sxs-lookup"><span data-stu-id="b0875-448">String</span></span>|  
|<span data-ttu-id="b0875-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-449">TABLE_NAME</span></span>|<span data-ttu-id="b0875-450">String</span><span class="sxs-lookup"><span data-stu-id="b0875-450">String</span></span>|  
|<span data-ttu-id="b0875-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-451">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-452">String</span><span class="sxs-lookup"><span data-stu-id="b0875-452">String</span></span>|  
|<span data-ttu-id="b0875-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-453">DATA_TYPE</span></span>|<span data-ttu-id="b0875-454">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-454">Int16</span></span>|  
|<span data-ttu-id="b0875-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-455">TYPE_NAME</span></span>|<span data-ttu-id="b0875-456">String</span><span class="sxs-lookup"><span data-stu-id="b0875-456">String</span></span>|  
|<span data-ttu-id="b0875-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b0875-457">PRECISION</span></span>|<span data-ttu-id="b0875-458">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-458">Int32</span></span>|  
|<span data-ttu-id="b0875-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-459">LENGTH</span></span>|<span data-ttu-id="b0875-460">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-460">Int32</span></span>|  
|<span data-ttu-id="b0875-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="b0875-461">SCALE</span></span>|<span data-ttu-id="b0875-462">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-462">Int16</span></span>|  
|<span data-ttu-id="b0875-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-463">RADIX</span></span>|<span data-ttu-id="b0875-464">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-464">Int16</span></span>|  
|<span data-ttu-id="b0875-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-465">NULLABLE</span></span>|<span data-ttu-id="b0875-466">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-466">Int16</span></span>|  
|<span data-ttu-id="b0875-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-467">REMARKS</span></span>|<span data-ttu-id="b0875-468">String</span><span class="sxs-lookup"><span data-stu-id="b0875-468">String</span></span>|  
|<span data-ttu-id="b0875-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-470">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b0875-471">程序</span><span class="sxs-lookup"><span data-stu-id="b0875-471">Procedures</span></span>  
  
|<span data-ttu-id="b0875-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-472">ColumnName</span></span>|<span data-ttu-id="b0875-473">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b0875-475">String</span><span class="sxs-lookup"><span data-stu-id="b0875-475">String</span></span>|  
|<span data-ttu-id="b0875-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b0875-477">String</span><span class="sxs-lookup"><span data-stu-id="b0875-477">String</span></span>|  
|<span data-ttu-id="b0875-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-479">String</span><span class="sxs-lookup"><span data-stu-id="b0875-479">String</span></span>|  
|<span data-ttu-id="b0875-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b0875-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b0875-481">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-481">Int16</span></span>|  
|<span data-ttu-id="b0875-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b0875-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b0875-483">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-483">Int16</span></span>|  
|<span data-ttu-id="b0875-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b0875-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b0875-485">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-485">Int16</span></span>|  
|<span data-ttu-id="b0875-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-486">REMARKS</span></span>|<span data-ttu-id="b0875-487">String</span><span class="sxs-lookup"><span data-stu-id="b0875-487">String</span></span>|  
|<span data-ttu-id="b0875-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b0875-489">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b0875-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b0875-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b0875-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-491">ColumnName</span></span>|<span data-ttu-id="b0875-492">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b0875-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b0875-494">String</span><span class="sxs-lookup"><span data-stu-id="b0875-494">String</span></span>|  
|<span data-ttu-id="b0875-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0875-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b0875-496">String</span><span class="sxs-lookup"><span data-stu-id="b0875-496">String</span></span>|  
|<span data-ttu-id="b0875-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-498">String</span><span class="sxs-lookup"><span data-stu-id="b0875-498">String</span></span>|  
|<span data-ttu-id="b0875-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-499">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-500">String</span><span class="sxs-lookup"><span data-stu-id="b0875-500">String</span></span>|  
|<span data-ttu-id="b0875-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-501">COLUMN_TYPE</span></span>|<span data-ttu-id="b0875-502">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-502">Int16</span></span>|  
|<span data-ttu-id="b0875-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-503">DATA_TYPE</span></span>|<span data-ttu-id="b0875-504">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-504">Int16</span></span>|  
|<span data-ttu-id="b0875-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-505">TYPE_NAME</span></span>|<span data-ttu-id="b0875-506">String</span><span class="sxs-lookup"><span data-stu-id="b0875-506">String</span></span>|  
|<span data-ttu-id="b0875-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b0875-507">PRECISION</span></span>|<span data-ttu-id="b0875-508">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-508">Int32</span></span>|  
|<span data-ttu-id="b0875-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-509">LENGTH</span></span>|<span data-ttu-id="b0875-510">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-510">Int32</span></span>|  
|<span data-ttu-id="b0875-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="b0875-511">SCALE</span></span>|<span data-ttu-id="b0875-512">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-512">Int16</span></span>|  
|<span data-ttu-id="b0875-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-513">RADIX</span></span>|<span data-ttu-id="b0875-514">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-514">Int16</span></span>|  
|<span data-ttu-id="b0875-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-515">NULLABLE</span></span>|<span data-ttu-id="b0875-516">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-516">Int16</span></span>|  
|<span data-ttu-id="b0875-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-517">REMARKS</span></span>|<span data-ttu-id="b0875-518">String</span><span class="sxs-lookup"><span data-stu-id="b0875-518">String</span></span>|  
|<span data-ttu-id="b0875-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="b0875-519">OVERLOAD</span></span>|<span data-ttu-id="b0875-520">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-520">Int32</span></span>|  
|<span data-ttu-id="b0875-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-522">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b0875-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b0875-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b0875-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b0875-524">ColumnName</span></span>|<span data-ttu-id="b0875-525">DataType</span><span class="sxs-lookup"><span data-stu-id="b0875-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b0875-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b0875-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="b0875-527">String</span><span class="sxs-lookup"><span data-stu-id="b0875-527">String</span></span>|  
|<span data-ttu-id="b0875-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b0875-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b0875-529">String</span><span class="sxs-lookup"><span data-stu-id="b0875-529">String</span></span>|  
|<span data-ttu-id="b0875-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="b0875-531">String</span><span class="sxs-lookup"><span data-stu-id="b0875-531">String</span></span>|  
|<span data-ttu-id="b0875-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-532">COLUMN_NAME</span></span>|<span data-ttu-id="b0875-533">String</span><span class="sxs-lookup"><span data-stu-id="b0875-533">String</span></span>|  
|<span data-ttu-id="b0875-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-534">COLUMN_TYPE</span></span>|<span data-ttu-id="b0875-535">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-535">Int16</span></span>|  
|<span data-ttu-id="b0875-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-536">DATA_TYPE</span></span>|<span data-ttu-id="b0875-537">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-537">Int16</span></span>|  
|<span data-ttu-id="b0875-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b0875-538">TYPE_NAME</span></span>|<span data-ttu-id="b0875-539">String</span><span class="sxs-lookup"><span data-stu-id="b0875-539">String</span></span>|  
|<span data-ttu-id="b0875-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b0875-540">COLUMN_SIZE</span></span>|<span data-ttu-id="b0875-541">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-541">Int32</span></span>|  
|<span data-ttu-id="b0875-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="b0875-543">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-543">Int32</span></span>|  
|<span data-ttu-id="b0875-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b0875-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b0875-545">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-545">Int16</span></span>|  
|<span data-ttu-id="b0875-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b0875-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b0875-547">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-547">Int16</span></span>|  
|<span data-ttu-id="b0875-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-548">NULLABLE</span></span>|<span data-ttu-id="b0875-549">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-549">Int16</span></span>|  
|<span data-ttu-id="b0875-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b0875-550">REMARKS</span></span>|<span data-ttu-id="b0875-551">String</span><span class="sxs-lookup"><span data-stu-id="b0875-551">String</span></span>|  
|<span data-ttu-id="b0875-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b0875-552">COLUMN_DEF</span></span>|<span data-ttu-id="b0875-553">String</span><span class="sxs-lookup"><span data-stu-id="b0875-553">String</span></span>|  
|<span data-ttu-id="b0875-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b0875-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b0875-555">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-555">Int16</span></span>|  
|<span data-ttu-id="b0875-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b0875-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b0875-557">Int16</span><span class="sxs-lookup"><span data-stu-id="b0875-557">Int16</span></span>|  
|<span data-ttu-id="b0875-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b0875-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b0875-559">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-559">Int32</span></span>|  
|<span data-ttu-id="b0875-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b0875-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="b0875-561">Int32</span><span class="sxs-lookup"><span data-stu-id="b0875-561">Int32</span></span>|  
|<span data-ttu-id="b0875-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b0875-562">IS_NULLABLE</span></span>|<span data-ttu-id="b0875-563">String</span><span class="sxs-lookup"><span data-stu-id="b0875-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0875-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0875-564">See Also</span></span>  
 [<span data-ttu-id="b0875-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b0875-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
