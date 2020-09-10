# VIVA+ Open Human Body Models

Human body finite element (FE) models for injury assessment

The VIVA+ models are under active development, with frequent beta releases of preliminary models.

The documentation is available at vivaplus.readthedocs.io

Join the **users' community** [![project chat](https://img.shields.io/badge/zulip-join_chat-brightgreen.svg)](https://vivaplus.zulipchat.com)

## Quick start

Current beta version is `0.2.0`

Download the files (download link above)

or

Clone the repository:

```
git clone https://virtual.openvt.eu/wp-2/viva-plus.git
```

### Directory structure

The include files that are common to  (material/section/property definitions, contacts, constraints, etc.) are placed in the `common` directory. The files the seated/standing (for example, node coordinates), can be found in the respective directory, for e.g., `50F/Seated/`.

```
viva-plus
├───50F
│   ├───Seated
│   └───Standing
├───assets
├───common
├───docs
└───validation
```

## Model updates

Find information on ongoing updates in the [CHANGELOG](CHANGELOG.md) file.

## License

![LGPLv3)](docs/images/lgplv3.png)

The models are licensed under [GNU Lesser General Public License, v3](https://www.gnu.org/licenses/lgpl-3.0-standalone.html)
