set(LLVM_TARGET_DEFINITIONS ShapeCanonicalization.td)
mlir_tablegen(ShapeCanonicalization.inc -gen-rewriters)
add_public_tablegen_target(MLIRShapeCanonicalizationIncGen)

add_mlir_dialect_library(MLIRShape
  Shape.cpp

  ADDITIONAL_HEADER_DIRS
  ${MLIR_MAIN_INCLUDE_DIR}/mlir/Dialect/Shape

  DEPENDS
  MLIRShapeOpsIncGen

  LINK_LIBS PUBLIC
  MLIRArithmetic
  MLIRCastInterfaces
  MLIRControlFlowInterfaces
  MLIRDialect
  MLIRInferTypeOpInterface
  MLIRIR
  MLIRSideEffectInterfaces
  MLIRStandard
  MLIRTensor
  )
