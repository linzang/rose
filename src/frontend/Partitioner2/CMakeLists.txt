if (enable-binary-analysis)
add_library(rosePartitioner2 OBJECT
  AddressUsageMap.C BasicBlock.C CfgPath.C Config.C
  ControlFlowGraph.C DataBlock.C DataFlow.C Engine.C Exception.C
  Function.C FunctionCallGraph.C FunctionNoop.C GraphViz.C InstructionProvider.C
  MayReturnAnalysis.C Modules.C ModulesElf.C ModulesLinux.C ModulesM68k.C ModulesPe.C
  ModulesPowerpc.C ModulesX86.C Partitioner.C Reference.C Semantics.C
  StackDeltaAnalysis.C Thunk.C Utility.C)
else()
add_library(rosePartitioner2 OBJECT
  dummyPartitioner2.C
)
endif()

add_dependencies(rosePartitioner2 rosetta_generated)

install(FILES
  AddressUsageMap.h BasicBlock.h BasicTypes.h CfgPath.h
  Config.h ControlFlowGraph.h DataBlock.h DataFlow.h Engine.h
  Exception.h Function.h FunctionCallGraph.h GraphViz.h
  InstructionProvider.h Modules.h ModulesElf.h ModulesLinux.h ModulesM68k.h
  ModulesPe.h ModulesPowerpc.h ModulesX86.h Partitioner.h Reference.h
  Semantics.h Thunk.h Utility.h

  DESTINATION ${INCLUDE_INSTALL_DIR}/Partitioner2)
