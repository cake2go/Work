# Work
Scripts #DoD 16May2016
The clinical data for DOD cohort has been uploaded. Please find the coding table attached and the PRNDL query below.

SELECT p.study_name, p.patient_id, p.age, p.race, p.preop_psa, p.cstage, p.clings_p, p.clings_s, p.clings, p.capra, p.rp_year, p.fu_time,
s.sample_id, s.sample_type, s.tissue_type, s.tissue_attribute, 
s.date_received, s.specimen_id, s.specimen_type, s.specimen_measure, s.external_id, s.received_blocks, s.received_slides, s.received_punches, s.received_stained_slides, s.received_rna, s.site_comment, s.failure_reason, s.status,
r.rna_id, r.rna_concentration, r.rna_yield, r.rna_260, r.rna_280, r.rna_260_280, r.rna_260_230, r.rna_date, r.rna_batch, r.rna_volume, 
c.cdna_id, c.cdna_concentration, c.cdna_yield, c.cdna_260, c.cdna_280, c.cdna_260_280, c.cdna_260_230, c.cdna_batch, c.cdna_date, c.cdna_note, c.rna_input,
cel.celfile_name, cel.qc_batch_id, cel.qc_flag, cel.percentpresent, cel.rf22_percentpresent, cel.posneg_auc, cel.hybcontrol, cel.hybpercentpresent, cel.celfile_date,
pb.*
FROM samples_biostats s LEFT JOIN patients_biostats p USING(patient_id) JOIN rna r USING(sample_id) JOIN cdna c USING(rna_id) JOIN celfiles cel USING(cdna_id) JOIN predictions_blinded_biostats pb USING(celfile_name) WHERE s.study_name = 'UCSF-Carroll-DODtransform';

