[recSession](recSession.md) -> [sigTreated](sigTreated.md) -> [sigFeatures](sigFeatures.md) -> [patRec](patRec.md)

# recSession #
  * sF (sampling frequency)
  * sT (sampling time)
  * cT (contraction time)
  * rT (relaxation time)
  * nM (number of movements)
  * nR (number of repetitions)
  * nCh (number of channels)
  * dev (device used for the recordings)
  * comm (communication mode, Wifi or COM)
  * comn (COM port name, available only in case of COM communication)
  * mov (description of the movements performed)
  * date
  * cmt (comments)
  * tdata (total data, Samples x Channels x Movements)
  * RampParameters (available only in case of ramp recording session)
    * rampMin (RMS mean value between all channels of the Minimum Voluntary Contraction session)
    * rampMax (RMS mean value between all channels of the Maximum Voluntary Contraction session, RMSmean x Movements)
    * minData (data of the Minimum Voluntary Contraction session, Samples x Channels)
    * maxData (data of the Maximum Voluntary Contraction session, Samples x Channels x Movements)

Previously due to the heritage of the [EMG\_AQ](EMG_AQ.md) the following fields were included

  * cTp (contraction time percentage)
  * trdata(data extracted using the cTp)

These two fields are no longer in the [recSession](recSession.md) and became part of [sigTreated](sigTreated.md).