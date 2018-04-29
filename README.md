# docker-xmrig-amd

Docker container for [xmrig-amd](https://github.com/xmrig/xmrig-amd) with AMD RX Vegas on Linux, including [AMDGPU-Unified Linux drivers](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx), and donate level patch.

## Requirements

 * [docker](https://docs.docker.com/install/)
 * [AMDGPU-Unified Linux drivers](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx) on the host

On you host, install the drivers with a command similar to:

```
./amdgpu-pro-17.50-511655/amdgpu-pro-install -y --opencl=rcom
```

## Usage

### First

Pull the latest build:

```
docker pull bananajamma/xmrig-amd-rocm
```

### Running

Example:

```
docker run --device /dev/dri --device /dev/kfd --group-add=video -it --rm --name xmrig-amd-rocm bananajamma/xmrig-amd-rocm --donate-level 0 -o gulf.moneroocean.stream:10032 -u 4JLN35ooAiU15BX6Rzi6DTWUKsdLALvf6Stx1uLLrYP28scYTAtyjhM3ULkrpCQMQ1BGvn2hSaYGtSzwtPcZhFSwdoFypnBsb6wKfhTGix -p x -k
```

### Building

If you've clone this repo and made changes:

```
docker build . --tag bananajamma/xmrig-amd-rocm
```

## FAQ

#### Does this work with more than one Vega?

I don't know, I only have one Vega right now.  I think it requires PCIe x16, and a [ROCm capable CPU](https://github.com/RadeonOpenCompute/ROCm#supported-cpus).  Let me know.

## License

MIT
