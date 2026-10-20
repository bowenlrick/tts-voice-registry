# Voice Model Registry

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

[English](README.md) | [简体中文](README_zh-CN.md)

An open registry for community voice models with standardized metadata, provenance, compatibility, and licensing information.

> **Status:** Early development  
> The registry format and contribution guidelines are currently being designed.

## About

Voice Model Registry aims to provide a structured and transparent way to publish, discover, and share community-created voice models.

Instead of being only a collection of model files, each voice entry records information such as:

- Framework and model version
- Model type and architecture
- Supported languages
- Model artifacts and checksums
- Training-data provenance
- Voice / speaker authorization status
- Model and asset licenses
- Compatibility information
- Download locations
- Version history

The goal is to make community voice models easier to use, verify, maintain, and redistribute responsibly.

The registry is designed to support different voice-model architectures without requiring every framework to use the same model format.

## Framework Support

Initial support will focus on:

| Framework | Type | Status |
| --- | --- | --- |
| GPT-SoVITS | TTS / Voice Cloning | 🚧 Planned |
| RVC | Voice Conversion | Future |
| Fish Speech | TTS / Voice Cloning | Future |
| OpenVoice | TTS / Voice Conversion | Future |
| Other frameworks | — | Contributions welcome |

Framework-specific model files may use completely different formats.

The registry therefore standardizes metadata and provenance rather than attempting to define a universal model checkpoint format.

## Repository Structure

~~~text
tts-voice-registry/
├── registry/           # Voice model metadata
│   └── <voice-id>/
│       ├── manifest.yaml
│       └── README.md
│
├── schema/             # Registry metadata schemas
├── scripts/            # Validation and maintenance tools
├── docs/               # Documentation
│
├── CONTRIBUTING.md
├── MODEL_POLICY.md
├── LICENSE
└── README.md
~~~

Large model files are not intended to be stored directly in this Git repository.

Model checkpoints may instead be hosted on services such as Hugging Face or GitHub Releases and referenced from their registry entries.

## Voice Manifest

Each registered voice will contain a machine-readable manifest describing the voice model and its associated metadata.

Example:

~~~yaml
schema_version: 1

id: example-voice
name: Example Voice

status: released

engine:
  family: GPT-SoVITS
  version: example-version

model_type:
  - tts
  - voice-cloning

languages:
  - zh-CN

voice:
  type: original
  real_person_clone: false

artifacts:
  - type: model
    filename: example.pth
    sha256: "..."

provenance:
  training_data_source: original_or_authorized

licenses:
  model: MIT
  training_data: restricted
  artwork: null
~~~

The schema is currently under development and may change before the first stable release.

Different frameworks may define additional framework-specific artifact fields while preserving the common registry metadata.

## Model Provenance and Licensing

The license of this repository does **not** automatically apply to individual voice models, datasets, reference audio, character artwork, or other third-party assets.

Each voice entry must declare its own relevant licensing and provenance information.

In particular:

- Framework licenses do not automatically determine the license of a trained voice model.
- Publicly available audio is not automatically authorized for voice-model training or redistribution.
- Models based on identifiable real people must provide appropriate authorization information.
- Character artwork and other assets may have licenses separate from the voice model itself.
- Contributors are responsible for ensuring that they have the necessary rights to distribute submitted materials.
- A model may not claim rights or permissions that its creator does not possess.
- The presence of a model in this registry does not imply that every possible use of that model is legally permitted.

See `MODEL_POLICY.md` for the full model-submission policy.

## Planned First Voice

The first experimental entry is planned to be a community-created **Whale Girl / 鲸鱼娘** voice using GPT-SoVITS.

The voice model will be developed as an unofficial community project.

It is not affiliated with, sponsored by, or endorsed by DeepSeek.

The planned voice is intended to be an original community-created voice rather than a clone of an identifiable real person.

Model files, provenance information, compatibility information, and licensing details will be published after training and evaluation are complete.

## Roadmap

- [ ] Define the `manifest.yaml` specification
- [ ] Add JSON Schema validation
- [ ] Add the first GPT-SoVITS voice entry
- [ ] Add automated manifest validation with GitHub Actions
- [ ] Add model checksum verification
- [ ] Define contribution and model-acceptance policies
- [ ] Add Hugging Face model hosting integration
- [ ] Define framework-specific artifact specifications
- [ ] Support additional voice-model frameworks
- [ ] Add voice-model versioning rules
- [ ] Build a searchable web interface

## Contributing

The project is currently in its initial design stage.

Contributions, suggestions, schema proposals, framework integrations, and discussions about voice-model interoperability are welcome.

Before submitting a voice model, contributors will be expected to provide sufficient information about:

- Model framework and version
- Model provenance
- Training-data provenance
- Voice / speaker authorization
- Applicable licenses
- Required model files
- File checksums
- Known compatibility requirements

Contribution guidelines will be available in `CONTRIBUTING.md`.

## Hosting

This repository primarily acts as a registry rather than a large-file hosting service.

The intended structure is:

~~~text
GitHub
├── Registry metadata
├── Schemas
├── Documentation
├── Validation tools
└── Version history

External model hosting
├── Model checkpoints
├── Framework-specific artifacts
├── Optional reference audio
└── Other large files
~~~

Model hosting locations will be referenced by the corresponding voice manifest.

## License

The source code, schemas, documentation, and utilities created specifically for this repository are licensed under the [MIT License](LICENSE), unless otherwise stated.

Individual voice models, training datasets, reference audio, artwork, character assets, and other third-party materials may use different licenses.

The license of the framework used to train or run a model does not automatically determine the license of the trained model.

Always check the corresponding voice manifest before using, modifying, or redistributing a voice model.

## Disclaimer

This is an independent community project.

The presence of a voice model in this registry does not imply endorsement by any person, company, organization, character rights holder, model developer, or voice-framework developer referenced by the model.

Model contributors are responsible for ensuring that they have the necessary rights and permissions for the materials they submit.

The registry provides provenance and licensing metadata to improve transparency, but inclusion in the registry should not be interpreted as a legal guarantee regarding every possible use of a model.
