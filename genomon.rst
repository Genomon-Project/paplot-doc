**************************
Use Genomon data
**************************

The configuration file of each version is prepared in the analysis result file output by `Genomon-pipeline <https://github.com/Genomon-Project/GenomonPipeline/>`_ .

※To customize it see :doc:`config`.

``{path to the paplot installed directory}/config_template``

====================================== ===============================
file name                              version
====================================== ===============================
genomon_v2_0_0.cfg                     Genomon 2.0.0 ～ 2.0.3 
genomon_v2_0_5_v2_0_4.cfg              Genomon 2.0.4 ～ 2.0.5
genomon_v2_2_0_merge.cfg               Genomon 2.2.0
genomon_v2_3_0_merge.cfg               Genomon 2.3.0
genomon_v2_4_0_dna_merge.cfg           Genomon 2.4.0 (dna)
genomon_v2_4_0_rna_merge.cfg           Genomon 2.4.0 (rna)
====================================== ===============================

* It corresponded to paplot output of rna result from Genomon 2.4.0.

How to distinguish the version based on Genomon-pipeline result file

============================= ================== ================= =============== ==================
version                       mutation           sv                qc              post-analysis
============================= ================== ================= =============== ==================
Genomon 2.0.0 ～ 2.0.3        no header          no header         no result       no results
Genomon 2.0.4 ～ 2.0.5        with header        no header         with results    no results
Genomon 2.2.0                 with header        with header       with results    with results
============================= ================== ================= =============== ==================

* Since genomon 2.3.0, Genomon-pipeline version name is output to paplot/{sample file name}/index.html.

Run example:

.. code-block:: bash

  genomon_root={path to the directory where Genomon was executed}
  sample={name of genomon sample file}
  output_dir={path to output directory of paplot}
  project_name={name of project}
  paplot_install_dir={path to the paplot installed directory}
  
  # for Genomon 2.4.0
  ## dna
  paplot qc ${genomon_root}/post_analysis/${sample}/merge_qc.txt ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_4_0_dna_merge.cfg
  paplot sv ${genomon_root}/post_analysis/${sample}/merge_sv_filt_pair_controlpanel.txt ${output_dir} ${project_name} --config_file ./config_template/genomon_v2_4_0_dna_merge.cfg
  paplot mutation ${genomon_root}/post_analysis/${sample}/merge_mutation_filt_pair_controlpanel.txt ${output_dir} ${project_name} --config_file ./config_template/genomon_v2_4_0_dna_merge.cfg
  
  ## rna
  paplot qc ${genomon_root}/post_analysis/${sample}/merge_starqc.txt ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_4_0_rna_merge.cfg
  paplot sv ${genomon_root}/post_analysis/${sample}/merge_fusionfusion_filt.txt ${output_dir} ${project_name} --config_file ./config_template/genomon_v2_4_0_rna_merge.cfg
  
  # for Genomon 2.3.0
  paplot qc ${genomon_root}/post_analysis/${sample}/merge_qc.txt ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_3_0_merge.cfg
  paplot sv ${genomon_root}/post_analysis/${sample}/merge_sv_filt_pair_controlpanel.txt ${output_dir} ${project_name} --config_file ./config_template/genomon_v2_3_0_merge.cfg
  paplot mutation ${genomon_root}/post_analysis/${sample}/merge_mutation_filt_pair_controlpanel.txt ${output_dir} ${project_name} --config_file ./config_template/genomon_v2_3_0_merge.cfg

  # for Genomon 2.2.0
  paplot qc ${genomon_root}/post_analysis/${sample}/merge_qc.txt ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_2_0_merge.cfg
  paplot sv ${genomon_root}/post_analysis/${sample}/merge_sv_filt_pair_controlpanel.txt ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_2_0_merge.cfg
  paplot mutation ${genomon_root}/post_analysis/${sample}/merge_mutation_filt_pair_controlpanel.txt ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_2_0_merge.cfg

  # for Genomon 2.0.4 or Genomon 2.0.5
  paplot qc "${genomon_root}/summary/*/*.tsv" ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_0_5_v2_0_4.cfg
  paplot sv "${genomon_root}/sv/*/*.genomonSV.result.txt" ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_0_5_v2_0_4.cfg
  paplot mutation "${genomon_root}/mutation/*/*_genomon_mutations.result.txt" ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_0_5_v2_0_4.cfg

  # for Genomon 2.0.0 ～ 2.0.3
  paplot sv "${genomon_root}/sv/*/*.genomonSV.result.txt" ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_0_0.cfg
  paplot mutation "${genomon_root}/mutation/*/*_genomon_mutations.result.txt" ${output_dir} ${project_name} --config_file ${paplot_install_dir}/config_template/genomon_v2_0_0.cfg

.. |new| image:: image/tab_001.gif
