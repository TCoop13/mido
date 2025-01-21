from mido import Message, MidiFile, MidiTrack

# Create a new MIDI file and tracks for chords, melody, and bassline
mid = MidiFile()

# Define basic helper functions for creating notes
def add_chord(track, time, notes, velocity=64, duration=480):
    """Add a chord (multiple notes) to the track."""
    for note in notes:
        track.append(Message('note_on', note=note, velocity=velocity, time=time))
        time = 0  # Only the first note needs a delay time
    for note in notes:
        track.append(Message('note_off', note=note, velocity=velocity, time=duration))

def add_melody(track, notes, velocity=64, duration=480, time_between=0):
    """Add a melody (single notes in sequence) to the track."""
    for note in notes:
        track.append(Message('note_on', note=note, velocity=velocity, time=time_between))
        track.append(Message('note_off', note=note, velocity=velocity, time=duration))

# Define chords, melody, and basslines
# Key: A Minor
chords = [
    [57, 60, 64],  # Am
    [55, 59, 62],  # G
    [53, 57, 60],  # F
    [48, 52, 55]   # C
]

melody = [
    69, 69, 67, 64,  # Am melody line
    65, 67, 69, 72,  # G melody line
    72, 74, 76, 77,  # F melody line
    67, 69, 71, 72   # C melody line
]

bassline = [
    45, 43, 41, 36  # Root notes of Am, G, F, C
]

# Create and add the chord track
chord_track = MidiTrack()
mid.tracks.append(chord_track)
for chord in chords:
    add_chord(chord_track, time=480, notes=chord, duration=960)

# Create and add the melody track
melody_track = MidiTrack()
mid.tracks.append(melody_track)
add_melody(melody_track, notes=melody, duration=240, time_between=240)

# Create and add the bassline track
bass_track = MidiTrack()
mid.tracks.append(bass_track)
for bass_note in bassline:
    add_melody(bass_track, notes=[bass_note], duration=960, time_between=480)

# Save the MIDI file
mid.save("The_Love_Hut_Song.mid")
print("MIDI file saved as 'The_Love_Hut_Song.mid'")
        As defined by the MIDI Association's specification.

    message
    messages
        A MIDI message.

    midi
        The Musical Instrument Digital Interface. The specification is
        maintained by the `MIDI Association <https://midi.org>`_.

    nibble
        Half a byte (usually 4 bits).
        An 8-bit byte has 2 nibbles: an upper and a lower nibble.

    pip
        The `Python Package Installer <https://pypi.org/project/pip/>`_.

    port
    ports
        A MIDI port.

    pypi
        The `Python Package Index <https://pypi.org>`_.

    python
        The `Python programming language <https://www.python.org>`_.

    rtd
    read the docs
        `Read the Docs <https://www.readthedocs.org>`_ or RTD for short
        is a popular service to build, manage versions and host documentation
        generated from Sphinx (and now MkDocs) in the Python ecosystem.

    rtpmidi
        A standard protocol to send MIDI over a TCP/IP link.

        .. seealso::

            * :rfc:`4695`

            * :rfc:`4696`

    tcp
        Transmission Control Protocol.

        .. seealso:: :rfc:`9293`

    tick
    ticks
        The :term:`MIDI File` unit of time.

    sysex
    system exclusive
        Special :term:`MIDI` messages that are intended for consumption by a
        specific device. Details about the structure and meaning of these
        messages are often found in the device's manual.


.. todo:: Fill this glossary and add the ``:term:`` directive where
          appropriate.
