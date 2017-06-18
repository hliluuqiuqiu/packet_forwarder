# Packet Forwarder

Packet forwarder to make the link between a LoRa concentrator and [The Things Network](https://www.thethingsnetwork.org)'s backend.

This packet forwarder **isn't destined** to [The Things Gateway](https://www.thethingsnetwork.org/docs/gateways/gateway/)'s users, but for users who **already have a gateway** from another vendor, and that want to connect it to The Things Network.

![Demo GIF](https://github.com/TheThingsNetwork/packet_forwarder/raw/master/pktfwd.gif)

* [Install](#install)
* [Build](#build)
* [Run](#run)
+ [Contributing](#contribute)
+ [License](#license)

## <a name="install"></a>Install

Installation manuals are available for main available gateways:

+ [Kerlink IoT Station installation manual](docs/INSTALL_INSTRUCTIONS/KERLINK.md)
+ [Multitech Conduit installation manual](docs/INSTALL_INSTRUCTIONS/MULTITECH.md)
+ [Raspberry Pi + IMST ic880a installation manual](docs/INSTALL_INSTRUCTIONS/IMST_RPI.md)

## <a name="build"></a>Build

If you have a custom-made gateway, or if you want to contribute to the development of the packet forwarder, you will have to build the binary yourself.

+ [Kerlink IoT Station build instructions](docs/INSTALL_INSTRUCTIONS/KERLINK.md#build)
+ [Multitech Conduit build instructions](docs/INSTALL_INSTRUCTIONS/MULTITECH.md#build)
+ [Raspberry Pi + IMST ic880a build instructions](docs/INSTALL_INSTRUCTIONS/IMST_RPI.md#build)
+ [SPI environment build instructions](docs/INSTALL_INSTRUCTIONS/SPI.md)
+ [FTDI environment build instructions](docs/INSTALL_INSTRUCTIONS/FTDI.md) *(Experimental)*

+ [General build parameters](docs/INSTALL_INSTRUCTIONS/PARAMETERS.md)

### <a name="run"></a>Run

```bash
$ packet-forwarder configure
$ packet-forwarder start
```

#### Configuration format and flags

The configuration file generated by `packet-forwarder configure` is stored at `$HOME/.pktfwd.yml`. You can specify a different config file with the `--config` flag, or specify runtime parameters with the different flags:

* `--id`: Gateway ID of the present gateway.
* `--key`: Gateway key of the present gateway.
* `--router`: ID of the router with which communicate (optional ; default: account server-stored router)
* `--auth-server`: URI of the account server (optional ; default: `https://account.thethingsnetwork.org`)
* `--discovery-server`: Address and port of the discovery server (optional ; default: `discover.thethingsnetwork.org:1900`)
* `--verbose` or `-v`: Show debugging information (optional)
* `--downlink-send-margin`: Change downlink send margin, in milliseconds (optional ; [see documentation](docs/IMPLEMENTATION/DOWNLINKS.md))
* `--ignore-crc`: Ignore CRC check, and send uplink packets upstream even if they are CRC-invalid.
* `--reset-pin`: Set a BCM pin number, that will be reset before starting the concentrator (for Raspberry Pi setups)

##### GPS configuration

You can configure a GPS for the packet forwarder in two different manners:

* With the GPS connected as a serial port: by setting `--gps-path`.
* With `gpsd`, by adding `--gpsd.enable`. You can specify the address of `gpsd` with `--gpsd.address`. `gpsd` has priority over the serial port.

## <a name="contribute"></a>Contributing

Source code for this packet forwarder is MIT licensed. We encourage users to make contributions on [Github](https://github.com/TheThingsNetwork/packet_forwarder) and to participate in discussions on [Slack](https://www.thethingsnetwork.org/forum/t/slack-invitations/3037/4).

If you encounter any problems, please check [open issues](https://github.com/TheThingsNetwork/packet_forwarder/issues) before [creating a new issue](https://github.com/TheThingsNetwork/packet_forwarder/issues/new). Please be specific and give a detailed description of the issue. Explain the steps to reproduce the problem. If you're able to fix the issue yourself, please help the community by forking the repository and submitting a pull request with your fix.

For contributing a feature, please open an issue that explains what you're working on. Work in your own fork of the repository and submit a pull request when you're done.

If you want to contribute, but don't know where to start, you could have a look at issues with the label [*easy*](https://github.com/TheThingsNetwork/packet_forwarder/labels/easy).

## <a name="license"></a>License

Source code for the packet forwarder is released under the MIT License, which can be found in the [LICENSE](LICENSE) file.
