# Nunataryuk

SUMMARY:
This repo contains mainly the CTD profiles of legs 1, 2, 3 and 4 of the Nunataryuk project.
Other parameters will be added later (e.g., particle size distribution, backscattering coefficient, etc.)

CONTENT:
The main results that will be of interest for the users are the following:
1) "./res/ASCII.final/individual.files/" - this folder contains 1 file per station/leg/date set. These files contain temperature, salinity as well as metadata,
2) "./res/ASCII.final/overall.file/" - this folder contains a unique file, called "Nunataryuk_Masterfile_v1-01.csv", which contains the same parameters as above, but all gathered in a unique file,
3) "./res/Nunataryuk_Metadata_v1-01.csv" - this file contains all the metadata for each station/leg/date set,
4) "./res/PDF.final/Nunataryuk_Masterfile_v1-01.pdf" - this PDF file displays a 1-pager overall view of all the temperature and salinity profiles per station/leg/date set.

PROCESSING NOTES:
1) The CTD profiles have been smoothed using a running median (spike removal), then a spline or loess function (mainly to output the values on a regular depth grid). The running median range and the smoothing function and its span are given for each cast in the file "./files/metadata.and.log/iop.info.csv",
2) As the CTD probes that were used don't have a depth tare feature, all the profile data that were gathered in air (visually) have been correlated to atmospheric pressure measurements found on the Environment Canada web site (see comments in "./src/02_compute_corr_depth_tare.R"). A correlation coefficient (r2) of 0.9173 (see "./res/temporary_results/comp_pressure_in_air.pdf") provides a good confidence in that method.
3) During the leg1, and sometimes during the leg2, several profiles have been performed at a single station/leg/date set. These profiles have been visually sorted (i.e. some have been discarded) then averaged,
4) During the processing, it was obvious that the upward casts were dragging water masses from the bottom of the water column toward the surface (see for example page 46 of the initial catalogue (profiles #91 and #92 of "./res/temporary_results/Nunataryuk_WP4_CTD_catalogue.pdf"). All the upward profiles have then been discarded (consistent with the IOP package user's guide anyway),
5) For some station/leg/date set, no IOP based CTD profiles were availables (e.g., the sensor was stuck in ice chunks). For these casts, and whenever available, data from a handheld CTD device were used and these data are included in the results files provided here.

NOTES:
1) Some results are not final delivery ones but might still be of interest, they have been put in "./res/temporary_results",
2) The parameters provided in the ASCII files follow the format "parameter [unit]" and are the foloowing:
    - "filename [NA]": standardized filename of the individual file,
    - "station [NA]": name of the station,
    - "cruise_station [NA]": name of the leg followed by the name of the station,
    - "latitude [decimal degree]": latitude in decimal degree,
    - "longitude [decimal degree]": longitude in decimal degree,
    - "utc_date_time [yyyy-mm-dd hh:mm]": UTC date and time with the specified format (time of the 1st profile when several),
    - "flag_qc [NA]": quality flag. 1 = profile has been kept ; 0 = profile has been discarded,
    - "comment [NA]": field comment,
    - "depth [m]": depth of the provided data (the grid has been set every 0.01 m),
    - "temperature [C]": smoothed temperature value,
    - "temperature_sdev [C]": smoothed temperature standard deviation (when several profiles),
    - "temperature_surface_handheld [C]": temperature measured with the handheld meter at the surface,
    - "salinity [NA]": smoothed salinity value,
    - "salinity_sdev [NA]": smoothed salinity standard deviation (when several profiles),
    - "salinity_surface_handheld [NA]": salinity measured with the handheld meter at the surface,

Guislain.Becu@takuvik.ulaval.ca

14 Apr. 2020
