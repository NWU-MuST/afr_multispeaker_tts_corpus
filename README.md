Multi-speaker Afrikaans TTS corpus
==================================

This is a brief description of the multi-speaker Afrikaans
text-to-speech (TTS) corpus. The aim of this corpus was to investigate
the implementation of a TTS system using multiple voices recorded
using a low-cost process (i.e. using non-professional volunteers and
informal recording environments).

The Afrikaans corpus was recorded in Hermanus, South Africa using
volunteers from the surrounding area in the last quarter of 2015.

A brief description focussing on aspects relevant for application of
the corpus follows. For more information on the development process
also see the following paper:

D.R. van Niekerk, C. van Heerden, M. Davel, N. Kleynhans,
O. Kjartansson, M. Jansche, L. Ha, "Rapid development of TTS corpora
for four South African languages," in Proceedings of the 18th Annual
Conference of the International Speech Communication Association
(Interspeech), pp. 2178-2182, Stockholm, Sweden, August 2017.

Furthermore,

 - The original release is available at: http://www.openslr.org/32/
 - This version can be found on http://www.demitasse.co.za/~demitasse/
 - The most up-to-date version of the text components (transcriptions
   and dictionaries) are available at: https://github.com/NWU-MuST

--------------------------------------------------------------------------------

## 1. Basic format and technical notes

This package should contain this file `README.md` and the following
subdirectories:
  - `dictionaries`
  - `recordings`
  - `transcriptions`


### 1.1 Dictionaries

This contains the phone sets and dictionaries covering the
pronunciation of all tokens in the normalised transcriptions.

  - `*.phoneset.p2p` contain the complete set of phones used in
    International Phonetic Alphabet (IPA) [1] and X-SAMPA [2].
  - `*.regular.dict` contain the standard pronunciations that are
    suitable for grapheme-to-phoneme rule extraction.
  - `*.irregular.dict` contain the standard pronunciations that do not
    follow the spelling rules of the language (may not be suitable for
    G2P extraction).
  - `*.addendum.dict` contain entries for speaker-specific and other
    deviations from standard pronunciations found in the corpus.

For more information on the protocol followed during development refer
to Section 5 and the accompanying technical report.


### 1.2 Recordings

These are the recordings in [FLAC format](https://xiph.org/flac/),
16-bit per sample at 48kHz sampling rate with basenames corresponding
to utterance entries in the transcriptions files.

No post-processing or audio editing has been done after recording, it
may thus be advisable to apply gain normalisation and some form of
dereverberation filtering before further processing. Recordings also
have variable lengths of silence (which may contain ambient noises) at
the start and end of each utterance.


### 1.3 Transcriptions

Two versions of the orthographic transcriptions are provided. The
first version (`utts.data.orig`) is in the original form as at the
time of recording. The normalised and reviewed forms corresponding to
the provided dictionaries are in `utts.data.norm`.

Text files are in UTF-8 encoded Unicode (NFC).

--------------------------------------------------------------------------------

## 2. Text resources

The corpus contains Afrikaans and English sentences, developed as
follows:

Afrikaans sentences originated from Wikipedia (downloaded
Sept. 2015) and other free content, and selected as follows:

  1. Full sentences were extracted and divided into subsets according
     to length (number of words).
  2. Sentences in each length subset were selected for phonetic
     coverage (diphone units), selecting more shorter sentences than
     longer.

Additional sentences were generated and added to represent the
following domains and types: navigation, weather, questions, sport and
numbers. Proper names originating from different languages were
included to provide cases of foreign or code-switched tokens.

English sentences were sourced from the CMU Arctic TTS corpora [3, 4],
of which all "set A" sentences were used.

After the recording and initial quality control (QC) process a subset
of usable utterances were obtained. Specifically, some utterances were
discarded due to the presence of buffer-underrun artifacts that were
not detected during the recording process.

--------------------------------------------------------------------------------

## 3. Speakers and corpus stratification

Each speaker read a subset of sentences of each language. For
Afrikaans a small set of (overlap) sentences containing the rarest
phones were read by all speakers.

After discarding utterances with audio quality issues, the corpus
consists of the following (duration excludes non-speech/silence):

|         | Utterances |         | Duration (minutes) |         |
|--------:|-----------:|--------:|-------------------:|--------:|
| Speaker |  Afrikaans | English |          Afrikaans | English |
|      01 |        297 |      65 |              16.00 |    2.81 |
|      02 |        248 |      60 |              18.11 |    3.51 |
|      03 |        254 |      66 |              15.66 |    3.05 |
|      04 |        246 |      64 |              14.91 |    3.16 |
|      05 |        250 |      67 |              15.38 |    3.16 |
|      06 |        258 |      65 |              15.33 |    3.18 |
|      07 |        247 |      68 |              16.33 |    3.51 |
|      08 |        248 |      64 |              15.91 |    3.16 |
|      09 |        250 |      64 |              14.91 |    3.06 |
|   Total |       2298 |     583 |             142.66 |   28.71 |

The following are subjective notes on speakers' delivery and accent
that may be useful (speaker id's are present in utterance labels):

| Speaker |  Voice quality |        Accent (Influence/Comment)           |     Delivery    |     English    |
|:-------:|:--------------:|:-------------------------------------------:|:---------------:|:--------------:|
|    1    | Young (hoarse) |           Standard (Informal)               |     Informal    |  Slight accent |
|    2    |       ---      |       Cape (sometimes [{] -> [E])           |     Careful     | Good (trained) |
|    3    |       ---      |                  (Cape)                     | Radio presenter |  Slight accent |
|    4    |       ---      |                  (Cape)                     |     Informal    |    Accented    |
|    5    |      Young     |                 Standard                    |     Informal    |  Slight accent |
|    6    |       ---      |                 Standard                    |     Informal    |    Accented    |
|    7    |     Mature     | Cape (sometimes _'n_ -> [`?@n`] or [`h@n`]) |    Assertive    |    Accented    |
|    8    |      Young     |         Cape (Brei: /R/ for /r/)            |     Informal    |    Accented    |
|    9    |       ---      |                  (Cape)                     |     Informal    |    Accented    |

--------------------------------------------------------------------------------

## 4. Orthographic transcriptions and quality checking

The following describes the basic process followed after recording:

  1. Manual _text normalisation_ (expanding numbers, dates and mark-up
     of foreign and "special" words)
  2. Semi-automatic _verification of transcriptions and dictionaries_
     by manually reviewing words flagged by automatic techniques as
     potential inaccuracies [5, 6].

These are described in the following subsections.


### 4.1 Text normalisation and mark-up

  * Numbers are expanded using `-` between words to preserve original
    tokens. Tokens should be split on `-` before determining
    pronunciations using the accompanying pronunciation dictionaries.
  * Capitalisation and punctuation is kept (though simplified in some
    cases). No attempt has been made to mark intonation
    phrases/breathgroups.
  * The presence of `_` in a token indicates a word which a "special"
    pronunciation, this includes:
	 - Pronunciation of letters (usually starting with `char_`)
	 - Alternative pronunciations per speaker/utterances (usually
           ending in digits, e.g. `_0`)
	 - Alternative pronunciations per accent (usually ending in
       letters, e.g. `_a`)
  * Tokens preceded by the _pipe symbol_ (`|`) are foreign words,
    i.e. words requiring a non-native phoneset. In this corpus all
    foreign words are assumed to be English (using the English phone
    set). Words were marked in this way purely on phonetic grounds,
    possible prosodic units were not considered.

Marking of foreign words was done on phonetic grounds only, i.e. no
attempt was made to mark words consistently with prosodic or syntactic
structures (e.g. proper noun phrases).


### 4.2 Transcription and pronunciation verification

As a final step, the transcriptions have been manually checked for
basic errors and an attempt has been made to specify the
pronunciations of tokens more accurately in certain contexts. However,
because this was a manual verification process, no gaurantees are made
regarding consistency or exhaustiveness. Potential corpus users should
verify the set of words marked in this way (identifiable by the
presence of an underscore `_`), especially when different
pronunciation resources are used.

Manual verification was done as follows:

  1. Transcriptions were reviewed by comparing expected durations of
     words with automatic phone alignments [5] and gross
     transcription and pronunciation deviations marked.
  2. Pronunciations of capitalised words were reviewed by comparing
     the mel-cepstral distance [5].
  3. Consistent speaker/accent specific deviations that were noticed
     during recording were marked, specifically in the orthographic
     contexts _'n_ and _...ek..._ (e.g. [`{`] vs [`E`]).

With the exception of these cases, all pronunciations were handled
systematically to be phonemically consistent as described in the next
section.

--------------------------------------------------------------------------------

## 5. Phone set and pronunciation dictionaries

The phone set and G2P rules used to develop the corpus is based on the
NCHLT project [7, 8, 9, 10]. The phoneset used here deviates from the
original NCHLT set by merging some phones into affricates and
diphthongs to simplify syllable specification (see
`dictionaries/phoneset.p2p`). Dictionaries were updated to match the
required vocabulary and stress and syllable markers added.

All dictionary entries aim to be consistent in the following ways:

  - Except for speaker-specific and other special entries in the
    pronunciation _addenda_ pronunciations are based on the dialect of
    Afrikaans spoken in the _Gauteng province_ of South Africa.
  - Where pronunciations deviate systematically between younger and
    older speakers, preference is given to more modern versions.
  - Phonetic detail (e.g. regarding unstressed vowel reduction,
    co-articulation, etc.) are not marked.
  - Words of foreign origin are transcribed as close to as possible to
    their original language pronunciations (in terms of both syllable
    and phones), with phones that do not exist in the target language
    (Afrikaans) remapped to their closest counterpart. See technical
    report for phone mappings.
  - During dictionary creation, compounds are treated as if their
    constituent parts are separate words, and within word articulatory
    effects not modelled at the lexicon level. (Similar to word
    boundary effects not modelled at the lexicon level.) Stress
    markers for compound words are ambiguous, and assignments were
    selected that generally match the current corpus. But also see
    below.

As described in Section 4.2, pronunciations of certain subsets of
tokens were reviewed in more detail and the resulting entries are
found in the pronunciation _addenda_. The rationale for reviewing
these subsets are:

  - Some exceptional pronunciations occur frequently and
    systematically enough to have a possible impact on synthesis
    quality (e.g. dialect: modern vs older; geographical).
    Pronunciation variants for these words were added and tagged.
  - The corpus contains a significant number of proper names
    originating from different languages. Considering the difficulty
    in predicting pronunciations for proper names, these tokens were
    not phonetised and considered during text selection. The work of
    reviewing pronunciations against the actual recordings
    (phonetically) should thus not compromise the intended baseline
    phone distributions of the corpus.

The dictionaries released with this corpus are intended to provide an
experimental protocol and cover the tokens in the corpus. For actual
system development it may be advisable to refer to larger resources
such as the RCRL Afrikaans pronunciation dictionary [11, 12] or NCHLT
dictionaries [8, 9]. While these resources contain significantly more
tokens (and are therefore more appropriate for G2P prediction), they
do not contain stress or syllable markers.

--------------------------------------------------------------------------------

## 6. References

[1] https://en.wikipedia.org/wiki/International_Phonetic_Alphabet

[2] https://en.wikipedia.org/wiki/X-SAMPA

[3] http://festvox.org/cmu_arctic/

[4] J. Kominek and A.W. Black, "The CMU Arctic speech databases," in
    Proceedings of the 5th International Speech Communication
    Association Speech Synthesis Workshop, Pittsburgh, PA, USA, 2004,
    pp. 223-224.

[5] D.R. van Niekerk, "Experiments in rapid development of accurate
    phonetic alignments for TTS in Afrikaans," in Proceedings of the
    Twenty-Second Annual Symposium of the Pattern Recognition
    Association of South Africa, Vanderbijlpark, South Africa, 2011,
    pp. 144-149.

[6] M.H. Davel, C.J. van Heerden and E. Barnard, "Validating
    smartphone-collected speech corpora," in Proceedings of the
    Workshop on Spoken Language Technologies for Under-resourced
    languages (SLTU), Cape Town, South Africa, 2012, pp. 68-75.

[7] E. Barnard, M.H. Davel, C.J. van Heerden, F. de Wet and
    J.A.C. Badenhorst, "The NCHLT speech corpus of the South African
    languages," in Proceedings of the Workshop on Spoken Language
    Technologies for Under-resourced languages (SLTU), St. Petersburg,
    Russia, 2014.

[8] M.H. Davel, W.D. Basson, C.J. van Heerden and E. Barnard, "NCHLT
    Dictionaries: Project Report," North-West University, Technical
    Report, 2013. [Online]. Available:
    https://sites.google.com/site/nchltspeechcorpus

[9] http://rma.nwu.ac.za/index.php/resource-catalogue/
    nchlt-inlang-dictionaries.html

[10] E. Barnard & M.H. Davel, "NCHLT 2013 phone set," Technical
     Report, 2013. [Online].  Available:
     https://sites.google.com/site/nchltspeechcorpus

[11] M.H. Davel and F. de Wet, "Verifying pronunciation dictionaries
     using conflict analysis," in Proc. INTERSPEECH, Makuhari, Japan,
     September 2010, pp. 1898-1901.

[12] https://sourceforge.net/projects/d2ac-a2dc/files/
