# Pipeline

```grime

type PipelineStage : (
	shader: ShaderProgram,
)

impl PipelineStage {
	func new() -> PipelineStage
}

type Pipeline : [PipelineStage]


```
